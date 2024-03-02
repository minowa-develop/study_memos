# 【Debian】OpenSSHの入れ方

参考URL:https://minecraft.server-memo.net/bedrock_server_install/

```sh
sudo apt install gcc
sudo apt install perl
sudo apt install zlib1g-dev
sudo apt install make

wget https://www.openssl.org/source/openssl-1.1.1c.tar.gz
sudo tar xzfv openssl-1.1.1c.tar.gz -C /usr/local/src/
sudo cd /usr/local/src/openssl-1.1.1c
sudo ./config --prefix=/usr/local/openssl shared zlib
sudo make
sudo make install

cd /etc/ld.so.conf.d/
sudo torch openssl-1.1.1.conf
sudo vi openssl-1.1.1.conf
# 上記viで記述 /usr/local/openssl/lib

ldconfig
ldconfig -p  | grep libssl
```
