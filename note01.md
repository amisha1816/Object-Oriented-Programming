
## Object Oriented Programming Notes

#### What is OOP
Object Oriented Programming is a practice to design resuable software systems. Instead of going with the input, process, output logic it rather centers on the definition of the data (through objects). The overal goal of OOP is to create an object that we can define and provide functionality to solve problems.


__Object__ → An instance of a class where the object can either be a function, a data structure or a combination of such. Objects have attributes (data) and methods (code)

__Class__ → A description of all objects that can be made from this set class where an object can be created from

__Types of Methods__
- ```__init__(self)``` helps us to do any initialization for the object’s attributes (like set-up for the actuual code). ```(self)``` is also there to denote that ```__init__``` is applied and accessible to the object.

__Example__

```python

class Dog: # make sure class name is capitalized
    
    def __init__(self, given_name, breed, age): # these attributes are the initialization attributes
        # initializes the dog by providing its name, breed and age

        self.name = given_name
        self.breed = breed
        self.age = age
        # self always needs to be there

    def bark(self): # this is a method
        print('Woof!')

    def eat(self, food):
        print(f'{self.name} is eating {food}')

    def __str__(self):
        # This is a __str__() base override to give our Dog Objects a string equivalent value. This allows our Dogs to type casted to strings.'''
        return f'A {self.breed} named {self.name} with an age of: {self.age}.'

    def __repr__(self):
        ''' Making our Dog Objects being representable in other objects. This is done by overriding __repr__()'''
        return self.__str__()
        
    # We need __str__ and __repr__ lines in all our code

```

#### Encapsulation
Encapsulation is restricting the access to the classes/objects’ certain attributes and methods. The main reason is data protection and restricting certain methods to be callable (think hiding passwords from a user).

We need a setter and getter when using encapsulation:
- Setter draws the item so we can see it
- Getter draws the item so we can edit it
- The format is def __(set/get)variable_name(self):

``` python
class Student:
  def __init__(self,nameF, nameL, num):
    self.firstName = nameF
    self.lastName = nameL
    self.__studentNumber = num
  
  def __getStudentNumber(self):
    return self.__studentNumber
```

__Overloading__ → Two methods in one class that have the same method name, but different parameters
__Overriding__ → Two methods with the same method name and parameters.


__Polymorphism__ → A method that can be used across different classes and object that is dependent on the parameters. For example if we have a Dog and Cat class, both could have the method eat().

__Overrides__ → Overrides allow us to manipulate how the object behaves when met with built-in methods and operators. The benefits are that we can start to complete mathematical operations on custom Objects and
can start to compare equality between custom Objects

__Inheritance__ → When an object or class is based on another class; where its features are from a parent class. Like if a class is gaining features from a superclass (parent). There's multiple types of inheritance such as single, multiple, multilevel.

__Methods__
- super() references first parent, instead of rewriting

## Worksheet Questions

``` python

# Card Deck Example ♦️ ♥️ ♣️ ♠️

from random import shuffle as r_shuffle

class Card:
    
    def __init__(self, suit, value):
        self.suit = suit
        self.value = value

    def __str__(self):
        value = self.value
        # value only exists within our string method
        if self.value == 11:
            value = 'Jack'
        elif self.value == 12:
            value = 'Queen'
        elif self.value == 13:
            value = 'King'
        elif self.value == 14:
            value = 'Ace'

        return f'{value} of {self.suit}'
        

    def __repr__(self):
        return self.__str__()
        
class Deck:

    __SUITS = ['Spades', 'Hearts', 'Clubs', 'Diamonds']
    __VALUES = list(range(2,15))

    def __init__(self):
        self.deck = self.initialize_deck()

    def initialize_deck(self):
        result = []
        for suit in self.__SUITS:
            for value in self.__VALUES:
                result.append(Card(suit, value))

        return result

    def shuffle(self):
        if self.deck:
            r_shuffle(self.deck)
            return True
        else:
            print('We have no cards in our deck.')
            return False

    def draw(self):
        if self.deck:
            return self.deck.pop()
        else:
            print('We have no cards in our deck.')
            return None

```
- All caps variables are reserved for constants
- When writing a complex class, don't put all the code in ```__init__```, rather in another def block 

