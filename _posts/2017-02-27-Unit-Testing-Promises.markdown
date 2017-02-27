---
layout: post
title:  "How to wait for promises during unit test"
date:   2017-01-27 22:21:57 +1100
category: Testing
---
Image you are testing a Javascript function which calls a url and, that url returns a promise with ‘SOME VALUE’.

Lets start writing test. I will be using jasmine to write my tests.
Firstly, we will write test to make sure the function has been defined.
A simple test could be,
<pre>
import { TestClass }  from ‘test-function.js’;
describe ( ‘check function’ , () => {
  it(‘has been defined, () =>  {
    expect(TestClass.promiseFunction). toBeDefined();
  }
});
</pre>

This will fail because, we have not initiated the class instance.
So, we will do this in beforeAll()

<pre>
import { TestClass }  from ‘test-function.js’;
describe ( ‘check promiseFunction()’ , () => {
  let testClass;
  beforeAll(() => {
    testClass = new TestClass();
  });

  it(‘has been defined, () =>  {
    expect(testClass.promiseFunction).toBeDefined();
  }
});
</pre>

Next, we will call the url using javascript fetch API. But this time we assume to initiate the class instance when promise is returned. We will also write test to check if promise is returned.

<pre>
import { TestClass }  from ‘test-function.js’;
describe ('check promiseFunction()', () => {
  let testClass;
  let Promise;
  beforeAll(() => {
    testClass = new TestClass();
    Promise =  fetch(url)
      .then(response => response.json())
      .then(value => {
        testClass = new TestClass(value);
      });
  });

  it('has been defined', () =>  {
    expect(testClass.promiseFunction). toBeDefined();
  }

  it('returns a promise', () => {
    expect(returnPromise).toEqual(jasmine.any(Promise));
  });

  it('is returning correct value' , () => {
    expect(testClass.promiseFunction).toEqual(SOME VALUE);
  });
});
</pre>
When you run test, the first and second test case will pass, however,
the third test case will fail.

<b>What went wrong?</b><br>
The third test was executed before the promise was actually returned. So, how to fix it.
The solution is we need to wait for the promise to return before executing the second test.
<pre>
beforeEach(done => {
  returnPromise.then(() => {
    done();
  });
});
</pre>
So , the test looks as below
<pre>
import { TestClass }  from ‘test-function.js’;
describe ( ‘check promiseFunction()’ , () => {
  let testClass;
  let Promise;
  beforeAll(() => {
    testClass = new TestClass();
    Promise =  fetch(url)
    .then(response => response.json())
    .then(value = {
      testClass = new TestClass(value);
    });
  });

  it('has been defined', () =>  {
    expect(testClass.promiseFunction). toBeDefined();
  });

  it('returns a promise', () => {
    expect(returnPromise).toEqual(jasmine.any(Promise));
  });

  describe('on successful promise return : ', () => {
    beforeEach(done => {
      returnPromise.then(() => {
      done();
    });

    it('is returning correct value', () => {
      expect(testClass.promiseFunction).toEqual(SOME VALUE);
    });
  });
});
</pre>

Now, all the test cases should pass.
