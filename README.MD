# WebNotifier

![PyPI](https://img.shields.io/pypi/v/webnotifier.svg)
![PyPI - Python Version](https://img.shields.io/pypi/pyversions/webnotifier.svg)
![PyPI - Status](https://img.shields.io/pypi/status/webnotifier.svg)
![PyPI - License](https://img.shields.io/pypi/l/webnotifier.svg)

Webnotifier is a simple package for notifying any webpage change.

## Requirements

This package needs:

- Requests >= 2.21.0
- lxml >= 4.3.3

## Installation

To install Webnotifier, use pip

```shell
$ pip install webnotifier
```

## Usage

Instanciate the WebNotifier class and pass an url array and two callbacks. Also, you can pass the interval time (in seconds).

```python
from webnotifier import WebNotifier

my_urls = [{'name':'BBC','href':'https://www.bbc.com'}, {'name':'Medium','href':'https://medium.com'}]

def onError(err):
    """
    URL and Name params can be accessed within err.name && err.url
    """
    print("There was an error with {} on {}".format(err.name, err.url))

def onNewChange(url,name):
    print("Webpage {} on {} changed!".format(name,url))

interval = 60 #Check if webpage changes every 60 seconds

custom_webnotifier = WebNotifier(my_urls,onNewChange,onError,interval)
custom_webnotifier.start()
```

When a webpage changes, the onNewChange callback will be triggered. Otherwise, if there's any error in getting the URL, onError callback will be executed.