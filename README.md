# goalSeek.js

goalSeek.js is a javascript library that can be used to solve for the value of an independent variable - "x" - of a function - "f(x)" - such that f(x) equals some defined goal. In other words: do you know the desired output of a function but not the input to yield such an output? If so, then use this goal seek!

Currently, this goal seek uses Steffensen's Method to find the root of the error. 
See: http://en.wikipedia.org/wiki/Steffensen%27s_method

## Functions:
<dl>
  <dt><h3>1. goalSeek(Func, aFuncParams, oFuncArgTarget, Goal, Tol, maxIter)</h3>
  <dd><h6>Arguments</h6>
  <ul>
    <li><b>Func</b>: the name of the function in question.</li>
    <li><b>aFuncParams</b>: the parameters that are used as the unput to Func. This must be an array, note from the examples that the input to the function does not need to be an array, only here does it need to be in array form! The array can include all kinds of javascript data types (e.g. integers, arrays, objects, etc.). Please note that the this array must contain a guess for the independent variable in question.</li>
    <li><b>oFuncArgTarget {Position: integer, propStr: string}</b>: an object to locate the independent variable within aFuncParams which is to be sought. Position is the position of the independent variable within the parameters array. propStr is only needed for independent variables that are within objects, otherwise it can be omitted. It is the location of the independent variable's key in dot notation.</li>
    <li><b>Goal</b>: the desired output of the function.</li>
    <li><b>Tol</b>: [OPTIONAL] the magnitude of the tolerance for an acceptable output. e.g. if the desired output is 100, a 0.1 tolerance would accept any output within the inclusive range {99.9: 100.1}. The default if no argument is given is the magnitude of 0.1% of the goal.</li>
    <li><b>maxIter</b>: [OPTIONAL] the maximum number of iterations to perform. The default if no argument is given is 1,000 iterations.</li>
  </ul>
  <dd><h6>Return</h6>
  <dd>The function will return the value of the independent variable such that the function is within the tolerance of the goal, or it will return null if no such value was found within the maximum allowed number of iterations. 
  <dt><h3>2. Support functions</h3>
  <dd>There are two support functions within this library which help in getting and setting values within objects. They are setObjVal(Obj, propStr, Value) and getObjVal(Obj, propStr).
</dl>

## Examples:
  
```html
<!--HTML-->
<script>
	function fx1(i1, i2, i3) {
		return i1 * i2 * i3;
	};

	function fx2(i, o) {
		return i * o.a * o.b.b1;
	};

	console.log(goalSeek(fx1, [4, 5, 3], {Position: 2}, 140, 0.01, 1000));
	console.log(goalSeek(fx2, [4, {a: 5, b: {b1: 3}}], {Position: 1, propStr: "b.b1"}, 140, 0.01, 1000));
</script>

<!--Will Return-->
=>7

=>7

```
## Todo:
<dl>
	<dd>
	<ul>
		<li>Allow for independent variables to be sought within arrays.</li>
		<li>Simplify code.</li>
	</ul>
</dl>

## Licenses:
<dl><dd>This work is licensed under the (included) MIT license. Other works that have been included in this work have been properly identified and attributed. Licenses for these works have also been included in the licenses folder within the "deps" subfolder.
</dl>

```
The MIT License (MIT)

Copyright (c) 2014 Adam Hanna

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```