# aes 150
#### let's see how advanced the advanced encryption system is

chall.py file
```py
import base64
import os

from Crypto.Cipher import AES
from Crypto.Util.Padding import pad
from dotenv import load_dotenv

load_dotenv()
flag = os.getenv("FLAG")

length = "Mg=="
bs = 16

key = pad(open("/dev/urandom", "rb").read(int(base64.b64decode(length))), bs)
iv = open("/dev/urandom", "rb").read(bs)

cipher = AES.new(key, AES.MODE_CBC, iv)
ct = cipher.encrypt(pad(flag.encode("utf-8"), 16))

print(f"[+] iv = {iv.hex()}")
print(f"[+] ct = {ct.hex()}")
```


my solution was to just bruteforce the key as its only 2 bytes long

```
import base64
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad
from Crypto.Util.Padding import pad

given_iv = bytes.fromhex("7d71bf6a2f1393c07a330fc54baae70a")
given_ct = bytes.fromhex("d244c13293d94356cdb70ad01c5fe8977e2e5feb43d9cb3b9bb9cea648bdabc6")
flag_length = 16  # Assuming the original flag was padded to 16 bytes

for i in range(256):  # Bruteforcing all possible 2-byte keys
    for j in range(256):
        key = pad(bytes([i, j]),16)
        cipher = AES.new(key, AES.MODE_CBC, iv=given_iv)
        try:
            decrypted = unpad(cipher.decrypt(given_ct), flag_length)
            print(f"Decrypted flag: {decrypted.decode('utf-8')}")
            break
        except ValueError:
            continue
```

which gives the flag

```
flag - unreal{m3_wh3n_/d3v/ur4nd0m}
```
