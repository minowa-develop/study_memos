# misskeyサーバ構築

[公式の手順](https://misskey-hub.net/ja/docs/for-admin/install/guides/manual/)に従って、misskeyを構築するためのスクリプト

AlmaLinux9を使用、misskeyビルド時、主記憶は4GBくらい必要(2GBはだめだった)

```bash
#!/bin/bash

# install pnpm
curl -fsSL https://get.pnpm.io/install.sh | sh -

# install node.js
curl -fsSL https://fnm.vercel.app/install | bash
. ~/.bashrc
fnm install 22

# install ffmpeg
dnf install epel-release -y
dnf config-manager --set-enabled crb
sudo dnf install --nogpgcheck https://mirrors.rpmfusion.org/free/el/rpmfusion-free-release-$(rpm -E %rhel).noarch.rpm -y
sudo dnf install --nogpgcheck https://mirrors.rpmfusion.org/nonfree/el/rpmfusion-nonfree-release-$(rpm -E %rhel).noarch.rpm -y
sudo dnf install ffmpeg ffmpeg-devel -y

# install redis
dnf install redis -y
systemctl enable redis --now

# install postgresql
dnf install https://download.postgresql.org/pub/repos/yum/reporpms/EL-9-x86_64/pgdg-redhat-repo-latest.noarch.rpm -y
dnf install postgresql16-server -y

# initialyze postgresql (su以外はposgreユーザーで実行)
su - postgres
/usr/pgsql-16/bin/initdb -E UTF8 --locale=C -A scram-sha-256 -W
sudo -u postgres /usr/pgsql-16/bin/initdb -D /var/lib/pgsql/16/data -E UTF8 --locale=C -A scram-sha-256 -W
systemctl enable postgresql-16 --now
sudo -u postgres psql -c "create database misskey"

# rmeove postgresql(再設定用)
dnf remove postgresql16-server -y
rm -rf /var/lib/pgsql/ /usr/pgsql-16

# create user
useradd -m -s /sbin/nologin misskey

# install misskey
cd /home/misskey/ || exit 1
dnf install -y git
git clone --recursive https://github.com/misskey-dev/misskey.git
cd misskey || exit 1
git submodule update --init
NODE_ENV=production pnpm install --frozen-lockfile

# initialize misskey
cp .config/example.yml .config/default.yml
sed -i 's/example-misskey-user/postgres/' .config/default.yml
sed -i 's/example-misskey-pass/test/' .config/default.yml
NODE_ENV=production pnpm run build
pnpm run init

# open firewall
firewall-cmd --add-port=3000/tcp --permanent
firewall-cmd --reload

# start misskey
NODE_ENV=production pnpm run start
```
