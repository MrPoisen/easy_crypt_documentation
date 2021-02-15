# Old Chiphers
This section talks about every chipher under the easy_crypt.cipher.old section
## [Caesar](https://en.wikipedia.org/wiki/Caesar_cipher)
*This Cipher supports pyprind*

The standard alphabet is:  
`standard_alphabet = string.ascii_lowercase + string.ascii_uppercase + string.punctuation + string.digits + "ÄÖÜäöüßÃŸâ€"`

```` python
from easy_crypt.chipher.old import caeser as c
encr = c.encrypt("Hello",5) #Shift 5
print(encr) #prints "Mjqqt"
decr = c.decrypt(encr,5) #Shift 5 back
print(decr) #prints "Hello"
````
If you want to use pyprind, do it like this:
```` python
from easy_crypt.chipher.old import caeser as c
encr,bar = c.encrypt("Hello",5,progbar=True) #Shift 5
print(bar) # prints final bar; this isn't needed
print(encr) #prints "Mjqqt"
decr,bar = c.decrypt(encr,5,progbar=True) #Shift 5 back
print(bar) # prints final bar; this isn't needed
print(decr) #prints "Hello"
````
`encrypt()` can take 4 arguments:
> `encrypt(text, shift, alphabet=None, progbar=False)`

>:param text: The text that is supposed to be encrypted (type: **str**)
> 
>:param shift: The Change of the text (type: **int**)
> 
>:param alphabet: The used Alphabet for encryption (type: **str**)
> 
>:param progbar: If the pyprind library should be used (type: **bool**)
> 
>:return: The encrypted text (type: **str**)


`decrypt()` can take 4 arguments:
> `decrypt(text, shift, alphabet=None, progbar=False)`

>:param text: The text that is supposed to be decrypted (type: **str**)
> 
>:param shift: The Change of the text (type: **int**)
> 
>:param alphabet: alphabet: The used Alphabet for decryption (type: **str**)
> 
>:param progbar: bool: If the pyprind library should be used (type: **bool**)
> 
>:return: The decrypted text (type: **str**)

##[Vigener](https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher)
*This Cipher supports pyprind*

The standard alphabet is:  
`standard_alphabet = string.ascii_lowercase + string.ascii_uppercase + string.punctuation + string.digits + "ÄÖÜäöüßÃŸâ€"`

``` python
from easy_crypt.chipher.old import vigener as v
encr = v.encrypt("Hello","Hello") #Encrypts with the pw
print(encr) #prints ".iwwC"
decr = c.decrypt(encr,"Hello") #Decrypts with the pw
print(decr) #prints "Hello"
```
If you want to use pyprind, do it like this:
``` python
from easy_crypt.chipher.old import vigener as v
encr, bar = v.encrypt("Hello","Hello",progbar=True) #Encrypts with the pw
print(bar) # prints final bar; this isn't needed
print(encr) #prints ".iwwC"
decr,bar = c.decrypt(encr,"Hello",progbar=True) #Decrypts with the pw
print(bar) # prints final bar; this isn't needed
print(decr) #prints "Hello"
```
You can use the ``gen_keys()`` funcction to generate random keys:
```` python
from easy_crypt.chipher.old import vigener as v
key = v.gen_keys(10) # The can lenght can be defined; standard is 8
````
`encrypt()` can take 4 arguments:

>`encrypt(text, pw, alphabet=None, progbar=False)`

>:param text: The text that is supposed to be encrypted (type: **str**)
> 
>:param pw: The password for the encryption (type: **str**)
> 
>:param alphabet: The used Alphabet for encryption (type: **str**)
> 
>:param progbar: bool: If the pyprind library should be used (type: **bool**)
> 
>:return: The encrypted text (type: **str**)

`decrypt()` can take 4 arguments:

>`decrypt(text, pw, alphabet=None, progbar=False)`

>:param text: The text that is supposed to be decrypted (type: **str**)
> 
>:param pw: The password for the decryption (type: **str**)
> 
>:param alphabet: The used Alphabet for encryption (type: **str**)
> 
>:param progbar: bool: If the pyprind library should be used (type: **bool**)
> 
>:return: The decrypted text (type: **str**)


``gen_keys()`` can take two arguments:

>`gen_keys(lenght=8,alphabet = None)`

>:param lenght: the lenght of the key (type: **int**)
> 
>:param alphabet: the alphabet that should be used (type: **str**)
> 
>:return: returns aa random string (type: **str**)

## [Rail fence cipher](https://en.wikipedia.org/wiki/Rail_fence_cipher)

``` python
from easy_crypt.chipher.old import rail_fence as r
encr = r.encrypt("Hello",2) #first the text, second the rails
print(encr) # prints "Hloel"
print(r.decrypt(encr,2)) #prints "Hello"
```
The amount of rails can't be larger than the length of the text.

encrypt() takes two arguments:
>``encrypt(text:str, shift: int)``

>:param text: The text that is supposed to be encrypted(type: **str**)
> 
>:param shift: How many rails should be used (type: **int**)
>
>:return: returns the encrypted text (type: **str**)

decrypt() takes two arguments:
>`decrypt(text:str, shift: int)`

>:param text: The text that is supposed to be decrypted(type: **str**)
> 
>:param shift: How many rails should be used (type: **int**)
>
>:return: returns the decrypted text (type: **str**)

## [Affine cipher](https://en.wikipedia.org/wiki/Affine_cipher)
The standard alphabet is:  
`standard_alphabet = string.ascii_lowercase + string.ascii_uppercase + string.punctuation + string.digits + "ÄÖÜäöüßÃŸâ€"`

``` python
from easy_crypt.chipher.old import affine as a
encr = a.encrypt("Hello",2,5) #first the text, second the key a (which must be a comprime to the lenght of the alphabet), third the key b
print(encr) # prints "T.``1"
print(a.decrypt(encr,2,5)) #prints "Hello"
```

encrypt() can take four arguments:

>`encrypt(text:str, a:int, b:int, alphabet=None)`

>:param text: the text that is supposed to be encrypted(type: **str**)
> 
>:param a: key a, must be a coprime to the length of the alphabet (type: **int**)
> 
>:param b: key b (type: **int**)
> 
>:param alphabet: the alphabet that should be used (type: **str**)
> 
>:return: returns encrypted str (type: **str**)

decrypt() can take four arguments:

>`decrypt(text:str, a:int, b:int, alphabet=None)`

>:param text: the text that is supposed to be decrypted(type: **str**)
> 
>:param a: key a, must be a coprime to the length of the alphabet (type: **int**)
> 
>:param b: key b (type: **int**)
> 
>:param alphabet: the alphabet that should be used (type: **str**)
> 
>:return: returns decrypted str (type: **str**)


## [Atbash cipher](https://en.wikipedia.org/wiki/Atbash)
The standard alphabet is:  
`standard_alphabet = string.ascii_lowercase + string.ascii_uppercase + string.punctuation + string.digits + "ÄÖÜäöüßÃŸâ€"`

The cipher function encyrypts and decrypts.
``` python
from easy_crypt.chipher.old import atbash as a
encr = a.cipher("Hello") #only needs the text; it can take an alphabet as a argument
print(encr) # prints "ä[::-"
print(a.cipher(encr)) #prints "Hello"
```

cipher can take two arguments:

>`cipher(text: str, alphabet=None)`

>:param text: the text that should be used (type: **str**)
> 
>:param alphabet: the alphabet that should be used (type: **str**)
> 
>:return: returns a string (type: **str**)