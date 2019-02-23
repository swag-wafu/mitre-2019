# Description

W(e( (h(a(v(e( (t(o( (g(o( (d(e(e(p(e(r)))))))))))))))))))

There is a file to download.

# Solution

If you `file flag`, you will get:
`flag: bzip2 compressed data, block size = 400k`

Ok, easy, you just to unzip it to flag1. If you `file flag1`, you will get:
`flag1: Zip archive data, at least v2.0 to extract`

At that point, you probably understand the meaning of the description of the challenge. The flag has been multiple times compressed and base64-coded. Too many times to do it manually.

I wrote a simple python script to do it. At each step, it uses `file` to know which transformation to apply: unzip or base64.

```python
import os
import subprocess

f = "flag"
nb = 0
while True:
    result = subprocess.run(['file',f+str(nb)], stdout=subprocess.PIPE)
    a = str(result.stdout)
    print(nb,a)
    if "zip" in a or "Zip" in a:
        # Unzip using 7z
        os.system('7z x -bb '+f+str(nb))
        os.system('mv flag '+f+str(nb+1))
        os.system('mv '+f+str(nb)+'~ '+f+str(nb+1))
        nb += 1
    elif "ASCII" in a:
        # base64 decode
        os.system('cat '+f+str(nb)+' | base64 -d > '+f+str(nb+1))
        nb += 1
    else:
        exit()
```

To use this script, rename `flag` into `flag0` and run `python3 script.py`.

There are 500 steps. The flag is in flag500: `MCA{Wh0_Needz_File_Extensions?}`
