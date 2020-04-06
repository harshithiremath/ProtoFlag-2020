# ProtoFlag 2020 Write-up
ProtoFlag 2020 was a basic Jeopardy-style __CTF__ hosted by the __Protocol Club, BMSCE__  
from 3rd - 5th March 2020, during the CoVid-19 Quaratine

# Day 1

### The First Flag
---
A link can seen in the Poster of the event. [Poster](<http://bit.ly/protoctf-1>)  
**Ans**: Visit the link, where a fake flag is displayed. Inspecting the sourcecode of the page reveals the real flag.

### Look Closely!
---
You can hide data in messages by adding them to the last few bytes of the images without changing the actual image as it mostly contains metadata.  
**Ans**: Open the image in a hex editor and scroll the last few bytes of the image to get your flag. If you are running Linux, you might as well pass the image into strings; run `strings img_name` in terminal  

### Some Cipher!
---
XOR Encryption is symmetric, which means if you try to encode the already encoded message using the key, you will end up with the decoded message.  
**Ans**: Use a reliable XOR decoder/encoder and decode the cipher using the key provided.

# Day 2

### Get The Joke?
---
The clue given was, 'HTTP Method'. GET is an HTTP Method which accepts parameters passed along with the link.  
Link: [Flag 2](<http://virus-ctf.000webhostapp.com/flag2.php>).  
**Ans**: Appending '?Joke=Right' to the link takes us to another page which has a textbox. Viewing the source code makes it obvious that 'Michael Scott' has to be entered into the textbox. The flag will be in the page in white.

### Edward Maya
---
Edward Maya had a Hit-single 'Stereo Love'. So, obviously the challenge had to do with stereo channels. The 'old fashioned encoding' mentioned referred to 'Morse Code'. After listening to the audio in a pair of headphones, one can hear that left and right audio signals are not the same. "The French man in South Carolina" refers to Beufort Cipher, which is a variant of Vigenere Cipher.  
Link: [Audio file](<https://drive.google.com/file/d/1wHz-ySMUcNmJOmihXp-1J1R_zLVCSBqi/view>).  
**Ans**:  Splitting the audio into left and right audio channels in audio tools like Audacity, we get two audio files. After decoding each audio file in a Morse Code decoder, we get 'RANDOMKEY' and an encrypted message. Replace the commas with {} and x's with _, and decipher the message using the Key, 'RANDOMKEY'.

### I Love Binary
---
Given hints were, "Maybe NOT".  
**Ans**: Simply invert the binary digits and convert them to ascii. The flag will be visible in the large paragraph.

# Day 3

### Misspelling Bee
---
Donald Trump's tweet 'covfefe' is referred to in the question.  
The given binary is `01100011011011110111011001100110011001010110011001100101`. The actual flag which is 'coverage', should be submitted in HEX form.  
**Ans**: Converting the given binary to ascii, we get "covfefe". Flag is "coverage" (Google *covfefe* if you are confused). Convert "coverage" to HEX form with no delimiter, and submit in the correct form.

### Crack the Code!
---
'Benedict Cumberbatch' hints to Enigma Cipher. Given flag: `ewnabpos{bmq_ninap_1d_op3a0v3}`.  
**Ans**: Use the _Enigma 1_ model to decode this cipher. Don't forget to choose the option of including foreign characters in the decoder.

### Infinity Hunt
---
Hints given were, "Found in a box, in a box" and "File extensions are deceiving", which mean the file is a zip. If you are running Linux, you can also find it out by passing the file into files; run `files file_name` in terminal.  
Given file: [Mystery File](<https://drive.google.com/file/d/1CoUDV3Hnbbzv6_R_LeMX8D1RK0rGzUum/view>)  
**Ans**: Replace the file extension with .zip, and view the file in zip viewer. You'll encounter many levels of folders in folders. You will find '1.txt' file, which contains 'railpass' encoded in binary, which is the password to zip file. Unpack it, and there's a file named no_flag.doc, which contains the flag.

### Snow
---
Clues given were, "Real light is in the dark" and "1998". These refer to Snow Steganography Cipher. Snow is a way of encrypting a message into a file, by appending tabs and spaces to the end of file.  
Given Base64 encrypted key, `S2V5MTIz`.  
The file: [Snow encrypted File]<https://drive.google.com/file/d/1UmF-s5tJOr4VlN34mfPx3P6WpbIUA4Tn/view>. Download Snow from [here](http://www.darkside.com.au/snow/)  
**Ans**: Decrypt the given key to get, 'Key123'. Using 'Key123' as the password, decipher the flag with Snow.  
Run `Snow -C -p "Key123" quest_out`

### Cute Crypt
---
Cute Crypt is a simple crypto, which converts letters into some characters.  
Lower-case letters are encrypted to `y num1 num2 num3`, and Upper-case letters to `x num1 num2`; adding these numbers we get 128 - ASCII(the_actual_letter).  
Given encrypted flag: <../Files/cute_crypt.txt> `y 4 4 4 y 5 6 6 x 24 25 y 7 7 7 x 25 26 x 29 30 y 10 10 11 y 6 6 6 x 28 28 y 5 6 6 x 21 22 y 4 5 5 x 22 22 y 5 6 6 x 25 26 x 31 32 y 7 7 7 x 29 30 y 4 4 4 y 8 8 8 x 27 28 x 22 23 y 4 4 5 y 8 8 8 x 27 28 x 22 22`.  
Crypto: [Cute Crypt](http://virus-ctf.000webhostapp.com/crypt_me.php)  
**Ans**: Write a python script or convert all of the characters manually to get the flag.

### I'm Split Up
---
The files are actually a 10x10 QR code split into a 100 files.  
**Ans**: Use a good image editor or write a program/script to piece all the images together and scan the QR code finally.

### Look Closely II
---
Zero width characters were used to increase the size of the message to one the memory can't handle. Hence crashing the device of the user that opened that message. This happened mostly on messaging apps like WhatsApp. Hackers also used this recently to bypass Office 365 protection services [More here](https://securityaffairs.co/wordpress/79791/hacking/z-wasp-attack-phishing.html)  
**Ans**: Use a tool like [this one](https://330k.github.io/misc_tools/unicode_steganography.html) to pull out the characters hidden using zero width encoding.
