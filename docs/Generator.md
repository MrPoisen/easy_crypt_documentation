## Generator
The Generator class is in the unknown module. It's main job is to create Passwords, not random but like a password list.  
There are two types of password lists, you could generate. One is every password of a alphabet, the second is all passwords  
of special chars on specific positions. 
``` python
from easy_cryptography.cipher.old.unknown import Generator
import string
gen = Generator(string.ascii_uppercase) #sets the alphabet 
for i in range(28):
    print(gen.convert()) # returns a string, first A than B,C,D ... at last AB
    gen.increase() 

gen.set_list([0,0,5])
print(gen.convert()) #prints AAF
print(gen.return_list()) #prints [0,0,5]

#now custom

gen.set_custom_alphabet(string.ascii_uppercase)
gen.set_custom_dic({0:["A","B"],1:["C","D"]})
print(gen.return_custom_pw()) #prints "AC"
gen.custom_increase()
print(gen.return_custom_pw()) #prints "BC"
```

The Generator class contains 10 functions. 6 are for the custom lists. 4 are for "normal" lists

Normal lists:

> `set_list(list_)`: 

- allows you to set a specific list to go on with  
- list_ must be a list  

> ``increase(amount_of_increases=1)``

- increases the list  
- amount_of_increases is how oft it is increased, normally one  

> ``convert()``

- converts the list to a str  

> ``return_list()``

- returns the list  

Custom lists:

> ``set_custom_alphabet(alphabet=None)``

- sets the alphabet for the custom list  
- if the alphabet is None, it will be set to the standard alphabet:  
  `string.ascii_uppercase + string.ascii_lowercase + string.punctuation + string.digits + "ÄÖÜäöüßÃŸâ€"`
  
> ``set_custom_dic(dic :dict)``

- takes a dict as an argument, it should be like this: ``{0:["A","B"],1:["C","D","l"]``-all letters must be in the custom alphabet  
- all letters must be in the custom alphabet  

> ``change_custom_values(costum_values :list)``

- takes a list as an argument  
- it sets the custom values to the new list -> for example: [1,1] to [2,0]  
- if the custom dic would be ``{0:["A","B"],1:["C","D","l"]``, [1,0] would be equal to "BC"  
- the length of the list should be equal to the amount of the custom dic keys  

> ``custom_increase(amount_of_increase=1)``

- takes an int as an argument  
- amount_of_increases is how oft it is increased, normally one  

> ``return_custom_pw()``

- returns custom list as a str corresponding to the custom alphabet  

> ``return_custom_list()``

- returns the custom list, used for generating the pws  
