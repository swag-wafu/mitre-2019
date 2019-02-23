# Description

Our team has gained limited access to an important system, can you help us escalate our privilege and find the flag?

`ssh ctf@138.247.13.107`

# Solution

In the server, you will find the file `HackMe`. It is an executable with SUID, which means it is executed with root privileges. Our objectif is to print the content of `/root/flag.txt`.

If you run the program, you get the output `Yadayadayada`. What is that? Better check its source. There is probably a better way to do it, but a good old `strings HackMe` will do the work. Without all the gibberish, you can find `head /var/log/auth.log`.

And indeed, if you execute this command, you get `Yadayadayada`. All we need to do is divert `head` so the program will run what it thinks is `head` with root privilege.

First, create a fake `head` with `echo bash > head`. But `HackMe` won't execute this file unless it finds it in the PATH variable. So let's modify the PATH variable with `PATH=/home/ctf:$PATH`. Finally, our script must be executable: `chmod +x head`.

That's it. When you run `HackMe`, it will execute our `head` and launch bash with root privilege.

`cat /root/flag.txt` yields `MCA{ON5cahqu4ooguaw}`.
