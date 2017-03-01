---
layout: post
title:  "Mock date with MomentJS - Jasmine Unit Test"
date:   2017-03-01 10:21:57 +1100
categories: Testing
---
MomentJS (https://momentjs.com/) is a great library to use for dates and time.
When doing unit test with Jasmine, it is east to make jasmine to mock date and
time with just 2 lines of code.

<pre>
beforeEach(() => {
 const mockedDateAndTime  = ‘2017-03-02 00:00:00’;
 const today = moment(mockedDateAndTime).toDate();
 jasmine.clock().mockDate(today);
});
</pre>

Now, jasmine uses the mockedDateAndTime to run all the tests, rather than
today's current date and time.
