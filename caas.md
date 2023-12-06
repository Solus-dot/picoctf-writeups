# cass

(flag: picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}) <br/>

We are given a website `https://caas.mars.picoctf.net/cowsay` which will print whatever input we type after the the `/cowsay/`. When we download the `index.js` file given in the question. We get the code:
```
const express = require('express');
const app = express();
const { exec } = require('child_process');

app.use(express.static('public'));

app.get('/cowsay/:message', (req, res) => {
  exec(`/usr/games/cowsay ${req.params.message}`, {timeout: 5000}, (error, stdout) => {
    if (error) return res.status(500).end();
    res.type('txt').send(stdout).end();
  });
});

app.listen(3000, () => {
  console.log('listening');
});
```

Here, we can see that the website is accessing the `/usr/games/cowsay` directory of the server, and since there is no filter, we can inject some code into it like `https://caas.mars.picoctf.net/cowsay/foo; ls`. This gives us a list of files present in `/usr/games/cowsay` directory and the thing of interest is `falg.txt`. We then input `https://caas.mars.picoctf.net/cowsay/foo; cat falg.txt` which gives us the flag `picoCTF{moooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo0o}`