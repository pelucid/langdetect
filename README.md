langdetect
==========

This is a GI Internal Fork of the PyPi-linked langdetect repo (that one is itself a port of Nakatani Shuyo's [language-detection](https://github.com/shuyo/language-detection) library (version from 03/03/2014) to Python). The reason for the fork is that in order to deploy this package on EMR, we had to wrap several of the auxilliary files into python scripts.


Installation
============

    $ pip install git+ssh://git@github.com/pelucid/langdetect.git

Supported Python versions 2.7, 3.4+.


Languages
=========

``langdetect`` supports 55 languages out of the box ([ISO 639-1 codes](https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)):

    af, ar, bg, bn, ca, cs, cy, da, de, el, en, es, et, fa, fi, fr, gu, he,
    hi, hr, hu, id, it, ja, kn, ko, lt, lv, mk, ml, mr, ne, nl, no, pa, pl,
    pt, ro, ru, sk, sl, so, sq, sv, sw, ta, te, th, tl, tr, uk, ur, vi, zh-cn, zh-tw


Basic usage
===========

To detect the language of the text:

```python
>>> from langdetect import detect
>>> detect("War doesn't show who's right, just who's left.")
'en'
>>> detect("Ein, zwei, drei, vier")
'de'
```

To find out the probabilities for the top languages:

```python
>>> from langdetect import detect_langs
>>> detect_langs("Otec matka syn.")
[sk:0.572770823327, pl:0.292872522702, cs:0.134356653968]
```

**NOTE**

Language detection algorithm is non-deterministic, which means that if you try to run it on a text which is either too short or too ambiguous, you might get different results everytime you run it.

To enforce consistent results, call following code before the first language detection:

```python
from langdetect import DetectorFactory
DetectorFactory.seed = 0
```

Anything else?
========================

For more details, please see the original repo that this was forked from
