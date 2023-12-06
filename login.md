# login

(flag: picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}) <br/>
When we click on the link of the website, we are greeted with a simple username and password login screen. looking at the source code, we find the file `index.js` which gives us. 
```
(async()=>{await new Promise((e=>window.addEventListener("load",e))),document.querySelector("form").addEventListener("submit",(e=>{e.preventDefault();const r={u:"input[name=username]",p:"input[name=password]"},t={};for(const e in r)t[e]=btoa(document.querySelector(r[e]).value).replace(/=/g,"");return"YWRtaW4"!==t.u?alert("Incorrect Username"):"cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ"!==t.p?alert("Incorrect Password"):void alert(`Correct Password! Your flag is ${atob(t.p)}.`)}))})();
```

As we can see in the last line, there is a alert of inputting the correct password with an encrypted messages which can be decrypted using the same function given in the source by putting the following in the console:
```
atob("cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ")
```
We get the flag `picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}`.