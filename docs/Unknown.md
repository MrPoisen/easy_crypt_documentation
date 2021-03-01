## Unknown class

The Unknown has severely functions for making it easy to decrypt ciphertexts if the encryption method is unknown.

```` python
import string
from easy_cryptography.cipher.old.unknown import Unknown

un = Unknown()
hex, bas64, coincidence= un.check("HELLO HOW ARE YOU",alphabet=string.ascii_uppercase) #checks if it could be hex and base64 
                                                                                       #and calculates the coincidenc 
print(hex,bas64,coincidence) #prints False False 0.0661764705882353

max_time = un.get_max_time("Hello HOW ARE YOU",fast=True,alphabet=string.ascii_uppercase) #calculates the value for the pyprind bar

print(un.test_for_divisors(5,[2])) prints False

print(un.find("Hello",["He"])) prints True

print(un.check_pw("ABC",string.ascii_uppercase) #Checks if the letters of the pw is in the alphabet; prints True

ciphertext = "PPQCAXQVEKGYBNKMAZUYBNGBALJONITSZMJYIMVRAGVOHTVRAUCTKSGDDWUOXITLAZUVAVVRAZCVKBQPIWPOU"
alphabet = string.ascii_uppercase
print(un.break_(ciphertext,alphabet=alphabet,fast=True,intell=["those"], ignore_capse=True, ignore_punctuation=True, ignore_numbers=True, Bruteforce=False))
#prints (Vigener,THOSEPOLICEOFFICERSOFFEREDHERARIDEHOMETHEYTELLTHEMAJOKETHOSEBARBERSLENTHERALOTOFMONEY,WICK) 
#First the encryption method, second the decrypted text, third the key/password
````
   
> ``get_max_time(text, alphabet=None, fast=True, addpwlist=None)``   

- calculates the max time needed for decryption. It should be used for the pyprind module  
- alphabet needs to be a str, fast a boolean and addpwlist a list  
- returns an int  

> ``test_for_divisors(a, divisors=None)``   

- tests if a value a can be divided by the divisors without rest  
- a must be an int or float, divisors must be a list  
- returns a bool  

> ``check(test)``   

- checks if the given text can be hex, base64 and returns the coincidence too
- test must be a string
- returns a bool for hex, another bool for base64 and a float for thee coincidence

> ``find(self, text: str, list_: list, split=" ", ignore_capse=False, ignore_punctuation=False, ignore_numbers=False, all_intell=None)``   

- searches if given words are in a text
- text must be a str
- list_ must be a list
- split must be a single char or False
- ignore_capse must be a bool
- ignore_punctuation must be a bool
- ignore_numbers must be a bool
- all_intell must be None, a bool, int or float not smaller than 0 and larger than 1
- returns a bool

> ``break_(text, **kwargs)``   

- tries to decrypt an unknown cipher
- text must be a str
- keywords:
    - `intell`: must be a list containing strings, all strings will be searched for in the decrypted message for identifying the right one
    - `all_intell`: must be a bool or an float or int not larger than 1 and smaller than 0; if True, it will return the decrypted msg where all string from intell are in; if float or int: will return string with enough matching words from intell
    - `ignore_caps`: must be a bool, if True, it will ignore upper and lowercase while checking for words in intell
    - `ignore_punctuation`: must be a bool, if True, it will ignore punctuations in the text while checking for words in intell
    - `ignore_numbers`: must be a bool, if True, it will ignore numbers while checking for words in intell
    - `alphabet`: must be a string, needs to contain all letters of the alphabet used for encryption
    - `bruteforce`: must be a bool, if True will bruteforce the vigener cipher if no other option is available
    - `fast`: must be a bool, if True will try less possible keys/passwords
    - `progbar`: must be a progbar from pyprind
    - `addpwlist`: must be a list containing strings, should contain possible passwords used for encrypting the text in vigener
    - `language`: must be a string, telling the used language (for now "en" and "ger"), used for frequency analysis
    - `split`: must be False or a string, tells where the decrypted text should be split for analyzing it's words
    - `add_frequency`: must be False or a dict, contains letter frequency's for frequency analysis; should look like this: `{"en":"ETAOINSHRDLCUMWFGYPBVKJXQZ"}` all in uppercase
    - `remain`: must be a list of chars, contains all chars which should not be decrypted
    - `max_length`: must be an int, contains the max_length keey length which should be used for a vigener analysis
