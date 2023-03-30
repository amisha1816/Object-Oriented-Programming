
## Object Oriented Programming


---

### Wed. March 29 Class
Content: Setting up Github 

```python 
# Example Class

class Person:
    def __init__(self, name):
        self.name = name
        
    def __str__(self)
        return f"Person Object called: {self.name}"
        
    def __repr__(self):
        return self.__str__()

```
---

### Thurs. March 30 Class
Content: Card Class

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
- When writing a complex class, don't put all the code in __init__, rather in another def block 

