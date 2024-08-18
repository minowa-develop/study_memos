# NSD設定

## /etc/nsd/nsd.conf

```conf
server:
        ip-address: ${ip}
        logfile: "/var/log/nsd.log"
        hide-version: yes
        hide-identity: yes
remote-control:
        control-enable: yes
zone:
        name: "domain"
        zonefile: "/etc/nsd/zones/domain.zone"

        # primary setting
        notify: ${secondary-ip} NOKEY
        provide-xfr: ${secondary-ip} NOKEY

        # secondary setting
        allow-notify: ${primary_ip} NOKEY
        request-xfr: ${primary_ip} NOKEY
```
