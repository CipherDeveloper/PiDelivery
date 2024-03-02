# PiDelivery
"Oh, I'm bored, lemme grab 1 million digits of Pi without frying my CPU"

Basically it is wrapper for Google's [pi.delivery](https://pi.delivery)
# Docs
```python
def fetch_pi(length: int = 1000, offset: int = 0):
    """
    Get part of Pi of specified length from specified offset
    :param length: Length of returned part (max 1000)
    :param offset: Offset of returned part (max 100 trillion)
    :return: Part of Pi
    """


def iter_pi(length: int = 10000, offset: int = 0, preload: bool = False):
    """
    Iterate digits from Pi
    :param length: Length of returned part (max 100 trillion)
    :param offset: Offset of returned part (max 100 trillion)
    :param preload: Whether you want to load numbers in background (useful if you are doing something in real time)
    :return Yields numbers one-by-one until limit is reached
    """

def get_pi(length: int = 10000, offset: int = 0):
    """
    Get digits from Pi
    :param length: Length of returned part (max 100 trillion)
    :param offset: Offset of returned part (max 100 trillion)
    :return Flattened list from iter_pi (use ''.join to turn it into string)
    """

class PiError(Exception):
    """
    This will be raised if site returns error
    """

# You can override pidelivery.LIMIT if Google decides to calculate more than 100 trillion digits
LIMIT = 100_000_000_000_000
```
# Examples
```python
import pidelivery as pi

# One raw request
print(pi.fetch_pi(length=10, offset=0))  # Prints 3141592653 (Google forgot to add dot)
# Iterator
for digit in pi.iter_pi(length=5000):
    print(digit, end='')  # Prints 5k digits one-by-one
# Iterator, flattened to list
print(pi.get_pi(length=5000, offset=0))  # Prints ['3', '1', '4', '1', ...] 
```