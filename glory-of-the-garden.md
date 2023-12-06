# glory-of-the-garden

(flag: picoCTF{more_than_m33ts_the_3y33dd2eEF5}) <br/>
This is an easy one. We need to download the file `garden.jpg`. When we run `file garden.jpg`, it is revealed that it is indeed a normal JPEG image. So our next course of action to use the `strings garden.jpg` command to find any hidden data and sure enough, the flag is found at the end after all the garbage strings on top.