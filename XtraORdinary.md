# XtraORdinary

(flag: picoCTF{w41t_s0_1_d1dnt_1nv3nt_x0r???}) <br/>
Judging by the title of the question we could deduce the encryption used for XOR. But I needed help for this question. We can see the source code of the encryption file as `encrypt.py` and we were given the encrypted flag `output.txt`. The for loops in the code were redundant since we only needed the last one and there were repeated strings in the `random_strs` list. So we just used this code and added the prefix of `picoCTF` to decode the entire flag.
```
import sys
from pwn import xor
from random import randint

#changes to hex format
c = bytes.fromhex("57657535570c1e1c612b3468106a18492140662d2f5967442a2960684d28017931617b1f3637")

#random strings
random_strs = [
    b'my encryption method',
    b'is absolutely impenetrable',
    b'and you will never',
    b'ever',
    b'break it'
]

#runs the "several" loops of the encrypt.py and uses xor
while True:
    for random_str in random_strs:
        for m in range(randint(0, pow(2, 0))):
            c = xor(c, random_str)

    #sets flag prefix and key
    flag_prefix = b"picoCTF{"
    key = xor(c[:len(flag_prefix)], flag_prefix)

    #Random key
    key = b'A'
    flag = xor(c, key)
    #verifies if decoded correctly
    if flag.startswith(b"picoCTF{"):
        print(flag.decode())
        sys.exit()
```

We get the output:
```
picoCTF{w41t_s0_1_d1dnt_1nv3nt_x0r???}
```