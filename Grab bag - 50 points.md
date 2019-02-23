# Description

Nyayanayanayanayanayanayanayan

`ssh ctf@138.247.13.114`

# Solution

If you try to connect to the server, you will be welcomed by an animated nyancat. If you want to analyze the output of the server, better save it into a file:

`ssh ctf@138.247.13.114 > output`

If you search for "MCA" (the flag format is MCA{…}), then you find the flag.

You can do it in one line with: 

`ssh ctf@138.247.13.114 | grep "MCA" | cat -v`

The command `cat -v` disables the ANSI escape code that mess the terminal.

The flag is: `MCA{Airadaepohh8Sha}`.
