## Analyse
The Analyse class contains several functions, only use the ones without _ at the beginning. 
It is used for decrypting a ciphertext encrypted with the vigenere cipher.

``` python
from easy_cryptography.cipher.old.unknown import Analyse
import string

an = Analyse(string.ascii_uppercase) #setting the alphabet

an.add_frequency({"fre":"ESAITNRULODCMPÉVQFBGHJÀXÈYÊZÇÔÙÂÛÎŒWKÏËÜÆÑ"})   # adding a frequency of letters for the 
                                                                        # french alphabet
ciphertext = "PPQCAXQVEKGYBNKMAZUYBNGBALJONITSZMJYIMVRAGVOHTVRAUCTKSGDDWUOXITLAZUVAVVRAZCVKBQPIWPOU" #original is english
Key_dict = an.get_keys(ciphertext,language = "en") #returns all possible passwords found, sorted after key length 
Key_list = an.key_dict_to_key_list(Key_dict) #returns a list with all passwords
```
The standard frequency's available are english and german

> ``add_frequency(frequency:dict)``

- frequency must be typ dict  
- keys are the language name  
- values are the alphabets in uppercase (if possible), sorted from most frequent to last frequent  

> ``get_keys(ciphertext,language="en")``

- takes first a ciphertext, second the language  
- ciphertext must be a string  
- the language must be the same as in a key in the frequency dict like "ger" or "en" in the standard one  
- returns a dictionary with the keys sorted after length  

> ``key_dict_to_key_list(dic :dict)``

- takes a dict as an argument, usually from the get_keys() function  
- returns a list with all passwords  

> ``change_max_length(length:int)``

- takes an int as an argument  
- sets the maximal possible password length for the analysis, the longer, the more time is needed  