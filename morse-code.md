# morse-code

(flag: picoCTF{wh47_h47h_90d_w20u9h7}) <br/>
We are given a `.wav` which, when played back, gives us several beeps, which is morse code. When plugging this file into audacity using `audacity morse_chal.wav`, we get several bands with spaces in between. We treat the thicker bands as dashes and the narrow ones are dots. Now we are able to decipher the flag. Decoding it letter by letter and following the rules mentioned in the question we get the flag:
`picoCTF{wh47_h47h_90d_w20u9h7}`