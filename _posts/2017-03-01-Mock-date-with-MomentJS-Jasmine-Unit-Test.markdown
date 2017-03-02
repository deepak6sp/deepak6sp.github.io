---
layout: post
title:  "Mock date with MomentJS - Jasmine Unit Test"
date:   2017-03-01 10:21:57 +1100
categories: Testing
---
MomentJS <a href="https://momentjs.com/" target="\_blank">( https://momentjs.com/ )</a>
is a great library for parsing, validating, manipulating, and formatting dates.
When running Jasmine unit tests, it is easy to mock date and time with just 3 lines of code.

<pre>
beforeEach(() => {
 const mockedDateAndTime  = ‘2017-03-02 00:00:00’;
 const today = moment(mockedDateAndTime).toDate();
 jasmine.clock().mockDate(today);
});
</pre>

Now, jasmine uses the mockedDateAndTime to run all the tests, rather than
today's current date and time.
