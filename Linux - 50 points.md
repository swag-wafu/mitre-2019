# Description

The year is 30xx. Clyde is trapped in an interdimensional transport module. The Federation has captured the module and has prepared to dock. The captain of the Federation lander has instructed the henchmen to bring Clyde in to Federation custody. As a precaution they will place Clyde in a clean room to remove any radiation. Luckily, you’ve hacked into the lander’s mainframe. Help Clyde escape!

`ssh ctf@138.247.13.108`

# Solution

If you log into the server, you will find youself within a restricted shell: `rshell`. You can't `cd`, `ls` or anything useful. Variables `SHELL` and `PATH` and read-only. With double-tab, you can see the list of the available commands. If you type anything and then tab, you will see the directory content.

You can remark a `bin` directory, containing `tee`, allowing you to write script with `echo (your code) | tee file`.

But you can also do `ssh ctf@138.247.13.108 'bash'` and bypass `rbash` completely. You can go to `/root` and display the content of `flag.txt`: `MCA{ieHaisoh4eif2ae}`.
