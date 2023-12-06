# bloat.py

(flag: picoCTF{d30bfu5c4710n_f7w_161a4f09}) <br/>
Here, when we read the file, we see that it is obfuscated as a string of regular expressions. When we run it, it asks for a certain password. Analyzing the code, we find that a certain function seems interesting to find the correct answer (as it has an if-else statement, I assumed it was the argument that checked the password):
```
def arg133(arg432):
  if arg432 == a[71]+a[64]+a[79]+a[79]+a[88]+a[66]+a[71]+a[64]+a[77]+a[66]+a[68]:
    return True
  else:
    print(a[51]+a[71]+a[64]+a[83]+a[94]+a[79]+a[64]+a[82]+a[82]+a[86]+a[78]+\
a[81]+a[67]+a[94]+a[72]+a[82]+a[94]+a[72]+a[77]+a[66]+a[78]+a[81]+\
a[81]+a[68]+a[66]+a[83])
    sys.exit(0)
    return False
```
The assumption proved true and we if we did `print(a[71]+a[64]+a[79]+a[79]+a[88]+a[66]+a[71]+a[64]+a[77]+a[66]+a[68])`, it gave us the phrase `happychance`. If we entered that in the password field we got:
```
Welcome back... your flag, user:
picoCTF{d30bfu5c4710n_f7w_161a4f09}
```