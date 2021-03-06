jQuery Password Entropy
=======================

This jQuery plug-in is built to give an estimate of the entropy of a password.
Initial calculations assume a randomly generated password is used, and then
applies a heuristics approach to penalize some common problems that arise
with human-generated passwords.

Some of the patterns used for creating the estimates are based on data collected
in the paper "Testing Metrics for Password Creation Policies by Attacking Large 
Sets of Revealed Passwords" by Weir et. al. and can be recommended as further
reading for those interested.

The default blacklisted passwords are based on lists downloaded from
http://www.skullsecurity.org/ and then compiled to match the purpose of this
plug-in. Only passwords with eight characters or more were kept in the list 
to save space, since my password policy doesn't allow anything shorter anyway.

Created by Erik Brännström.

Refactored by David Haslem to allow integration with jquery.validation

Options
-------

- display       : Selector for the element to display strength.
- functions     : Array of functions that receive the current entropy and password.
                  Must return a value that will replace the current value.
                  Options are merged with defaults.
- thresholds    : Array with thresholds counts, defining cutoffs for
                  each classification
- strings       : Array with same length as thresholds, setting the result string.
- classes       : Array with same length as thresholds, setting the class of the 
                  display element based on the strength.
- blacklist     : Array containing blacklisted words that should not be used as
                  passwords. Options are merged with defaults.



Examples
-------

    $('input[type=password]').passwordEntropy({
      'display' : 'div.result'
    });

    // Standalone usage
    var tester = $.entropyTestFactory();
    var entropy = tester.test('Foobar123');
    var classification = tester.classify(entropy);
    alert('Foobar123 has an entropy of '+entropy+' which is level '+classification);
    alert('Classification is '+tester.messageForClass(classification));

It is possible to integrate the standalone tester into other jquery
plugins. An example is available here: 

https://github.com/therabidbanana/jQuery-Password-Entropy/tree/validation-demo


License
-------
Copyright (C) 2011 by Erik Brännström

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
