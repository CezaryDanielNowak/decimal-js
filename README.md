Decimal
======

Simple decimal arithmetic for the browser *and* node.js!


Why?
=======

    Why don’t my numbers, like 0.1 + 0.2 add up to a nice round 0.3,
    and instead I get a weird result like 0.30000000000000004?

    Because internally, computers use a format (binary floating-point)
    that cannot accurately represent a number like 0.1, 0.2 or 0.3 at all.

Source : http://floating-point-gui.de/

I wrote this because I needed to do simple computation in the browser
and I couldn't find a lightweight library to do it.

How to use?
===========


In the browser
--------------

    <script src="lib/decimal.js"></script>

In node
-------

    npm install decimal

then in your program

    var Decimal = require('decimal');


Examples
=======

    >>> 1.1 + 2.2;
    3.3000000000000003

    >>> Decimal('1.1').add('2.2').toNumber();
    3.3

    >>> 4.01 * 2.01;
    8.060099999999998

    >>> Decimal('4.01').mul('2.01').toNumber();
    8.0601

    >>> Decimal.mul('4.01', '2.01').toNumber();
    8.0601

Order of Operations
===========
Decimal.js orders operations from left-to-right. You should note that, building complex equations.

    >>> 5+5*5
    30
    
    >>> Decimal('5').add('5').mul('5').toNumber()
    50


Can I help?
===========

Of course you can, I suck at math, and this implementation is very naive.
If you are a math Guru and you see something wrong or a
way to simplify things you can send in a pull request.


Methods
=======

Decimal(n)
------------------

Create a new `Decimal` from `n`. `n` can be a string, integer, or
another `Decimal`.

.toString()
------------------

Returns the `Decimal` instance as a string.

.toFixed()
------------------

Returns the `Decimal` instance as a string with fixed count of decimal part of number.
Similar to Number.toFixed()

    >>> 2.33333333333333.toFixed(20);
    "2.33333333333332992865"

    >>> Decimal('2.33333333333333').toFixed(20);
    "2.33333333333333000000"

    >>> 666666666666.0.toFixed(-2);
    "666666666700"

    >>> Decimal('666666666666.0').toFixed(-2);
    "666666666600"

.toNumber()
-----------

Turn a `Decimal` into a `Number`.

.add(n)
-------

Return a new `Decimal` containing the instance value plus `n`.

.sub(n)
-------

Return a new `Decimal` containing the instance value minus `n`.

.mul(n)
-------

Return a new `Decimal` containing the instance value multiplied by `n`.

.div(n)
-------

Return a new `Decimal` containing the instance value integrally divided by `n`.


.abs(n)
-------

Return a new `Decimal` containing the absolute value.
Similar to Math.abs.

    >>> Decimal('-600').abs();
    "600"
    
    >>> Decimal.abs('-600');
    "600"

.floor(n)
-------

Return a new `Decimal` containing the number rounded downward.
Similar to Math.floor.

    >>> Decimal('-1.5').floor().toString();
    "-2"
    
    >>> Decimal.floor('1.5').toString();
    "1"

.ceil(n)
-------

Return a new `Decimal` containing the number rounded upward.
Similar to Math.ceil.

    >>> Decimal('-1.5').ceil().toString();
    "-1"
    
    >>> Decimal.ceil('1.5').toString();
    "2"
