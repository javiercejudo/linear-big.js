
# linear-big.js

[![Build Status](https://travis-ci.org/javiercejudo/linear-big.js.svg?branch=master)](https://travis-ci.org/javiercejudo/linear-big.js)

A small, fast JavaScript library for arbitrary-precision decimal arithmetic.

The little little sister to [big.js](https://github.com/MikeMcl/big.js/) and [bignumber.js](https://github.com/MikeMcl/bignumber.js/).
See also [decimal.js](https://github.com/MikeMcl/decimal.js/), and [here](https://github.com/MikeMcl/big.js/wiki) for the difference between them.

## Load

The library is the single JavaScript file *linear-big.js* (or *linear-big.min.js*, which is *linear-big.js* minified).

It can be loaded via a script tag in an HTML document for the browser

    <script src='./relative/path/to/big.js'></script>

or as a CommonJS, [Node.js](http://nodejs.org) or AMD module using `require`.

    var Big = require('linear-big.js');

For Node.js, the library is available from the npm registry:

    $ npm install linear-big.js



## Use

*In all examples below, `var`, semicolons and `toString` calls are not shown.
If a commented-out value is in quotes it means `toString` has been called on the preceding expression.*

The library exports a single function: Big, the constructor of Big number instances.
It accepts a value of type Number, String or Big number Object.

    x = new Big(123.4567)
    y = Big('123456.7e-3')             // 'new' is optional

A Big number is immutable in the sense that it is not changed by its methods.

    0.3 - 0.1                          // 0.19999999999999998
    x = new Big(0.3)
    x.minus(0.1)                       // "0.2"
    x                                  // "0.3"

The methods that return a Big number can be chained.

    x.div(y).plus(z).times(9).minus('1.234567801234567e+8').plus(976.54321).div('2598.11772')

The maximum number of decimal places and the rounding mode used to round the results of the `div`
method is determined by the value of the `DP` and `RM` properties of the `Big` number constructor.  

(From *v3.0.0*, multiple Big number constructors can be created, see Change Log below.)

    Big.DP = 10
    Big.RM = 1

    x = new Big(2);
    y = new Big(3);
    z = x.div(y)                       // "0.6666666667"
    z.times(z)                         // "0.44444444448888888889"

The value of a Big number is stored in a decimal floating point format in terms of a coefficient, exponent and sign.

    x = new Big(-123.456);
    x.c                                // [1,2,3,4,5,6]    coefficient (i.e. significand)
    x.e                                // 2                exponent
    x.s                                // -1               sign

For further information see the [API](http://mikemcl.github.io/big.js/) reference from the *doc* folder.

## Test

The *test* directory contains the test scripts for each Big number method.

The tests can be run with Node or a browser.

To test all the methods from a command-line shell at the *test* directory,

    $ node every-test

For the browser, see *single-test.html* and *every-test.html* in the *test/browser* directory.

## Build

I.e. minify.

For Node, if uglify-js is installed globally ( `npm install uglify-js -g` ) then

    uglifyjs -o ./linear-big.min.js ./linear-big.js

will create *linear-big.min.js*.

## Feedback

Feedback is welcome.

Bugs/comments/questions?
Open an issue, or email

Michael
<a href="mailto:M8ch88l@gmail.com">M8ch88l@gmail.com</a>

Bitcoin donation to:
**1DppGRQSjVSMgGxuygDEHQuWEdTiVEzJYG**
Thank you

## Licence

See [LICENCE](LICENCE).
