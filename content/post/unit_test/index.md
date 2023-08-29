---
title: Unit Testing
summary: 'You want to save time while programming and be a bit less anxious about the correctness of your code? Unit tests are for you!'
subtitle: 
authors:
  - admin
tags: ['Tools','Python']
categories: []
projects: []
draft: false
featured: false
date: '2023-08-29T00:00:00Z'
lastMod: '2023-08-29T00:00:00Z'
image: 
  caption: 'generated with DALL-E'
  focal_point: ''
  preview_only: true
---  
Only very few problems in physics can be solved exactly. The harmonic oscillator comes to mind (maybe one or two others), but the list ends very quickly. If we cannot solve a system analytically (aka exactly), we turn to numerics. That usually includes writing your own code, or using someone else's code.
But how do we know that this code is doing the right thing? After all, you enter numbers and get other numbers that you cannot check. If you could, you would use that method  to solve the problem directly.

We are left with a bunch of numbers and we have to believe them. My problem: I usually don't. One of the first rules of scientific programming: **Don't fall in love with your code**. If a numerical simulation of a golf ball tells you that it will rest at 1000m above the ground without support, most probably it did not discover new physics. You have a buggy code.

So, what do we do about that?
## TL;DR
Unit tests are a standard way in software development to test the correctness of small functions individually. They help to build trust in the correctness of a program. In short: Don't trust a program without unit tests!

If we don't trust a code a priori, we have to find a way to build trust in the code. One way is the use of *unit tests*. Unit tests are small functions that check specific parts of your code. Instead of believing the whole code in one piece, we can start by trusting small parts of the code. By trusting more and more functions, we end up trusting the whole simulation.

Do we really need more code for that? We could just check the output of a couple of function calls and be happy. Yes, we could. But then we have to repeat all tests by hand after each change to the code. Unit tests are just a way to automize this testing by hand. After all, a code is growing and changing. If the tests run automatically, big and bold changes are much easier to check: if all tests run through, your code is at least as correct as before.

But wait, isn't that what `assert` statements do? Yes and no. An assertion checks that a given variable fulfills a criterion in all cases. For example, the golf ball is always flying above the ground. If this is not the case, you terminate the program.
Unit tests are focused on testing the outcome of functions with different sets of parameters. You might want to check that the ball stays in the same place if it is not hit, etc. Furthermore, unit tests do not run during your actual production run (while you are generating important data). Thus, they can take a bit of time without impacting the performance of the program.

## Unit testing in Python with `unittest`
Enough theory about the importance of unit testing. How does it work in practice? We will have a look at a simple example code that just adds numbers and flips an array. If you want to try the code on your own, you can save the code below in a file `foo.py`.

```python
import numpy as np

# This file (foo.py) just contains two arbitrary functions to be tested in test.py

def add_4(a):
    """Add four to the inpu

    Args:
        a (numeric): Input number

    Returns:
        numeric: Original number increased by 4
    """
    return a+4

def flip_array(arr):
    """Reverse the array

    Args:
        arr (np.ndarray): Input array

    Returns:
        np.ndarray: Flipped array
    """
    return np.flip(arr)


```
The functions are almost trivial, but we are less interested in the functions, but in the testing.

### The building blocks
Python's build-in unit testing is packaged in the module `unittest`. Our new file `tests.py` will start with an import of the module.
```python
import unittest
```
Now, we have to somehow define test cases, i.e. we call the functions that we would like to test and we provide the expected outcome. By comparing the two values, we can decide whether the test succeeded or failed.

In `unittest`, the test cases are modeled as classes. If classes (or object orientation) does not tell you much, don't worry. We will just use it and dive deeply into object orientation. If you are interested to learn more, have a look [here](https://realpython.com/python3-object-oriented-programming/).

For us, the object orientation means that we add the following lines to `tests.py`
```python
class TestMethods(unittest.TestCase):
	def test_add_4(self):
		pass

	def test_flip_array(self):
		pass
```
Here, we picked the name `TestMethods` randomly. You can pick any other name. However, you cannot change the name in the parenthesis (`unittest.TestCase`). The parentheses mean that our class `TestMethods` inherits properties from `unittest.TestCase`. If we talk about it, we can say `TestMethods` *is-a* `unittest.TestCase`. 
Since we are planning to test the two functions in `foo.py`, we already write to functions `test_add_4` and `test_flip_array`. In `unittest` all tests have to start with `test`, otherwise they are not executed as test later. In other words, you can change the lines to 
```python
def test_adding_four(self):
	pass
```
but not to
```python
def adding_four_test(self):
	pass
```
The function name has to start with `test`. The parameter (`self`) is related to the object-orientation and is a self-reference back to the original class. Just make sure to add it to every test function.

Now, we can finally make use of the comparison methods provided by `unittest` to ensure the correctness of the functions in `foo.py`.
We could just call the function on random numbers and make sure that the random number was incremented by 4.
```python
def test_add_4(self):
	# Test foo.add_4
	for i in range(100):       # Iterate over 100 random numbers
		rnd = np.random.rand() # Draw a random number
		val = foo.add_4(rnd)   # Call the function to be tested
		ref = rnd+4            # Compute a reference value 
		self.assertAlmostEqual(val,ref) # Compare the two values
```
The last line is the actual comparison between the reference value `ref`(we added 4 to the value by hand) and `val` (the output of the function acting on `rnd`). Note that we do not use `self.assertEqual` since we comparing floating point values.

The functions for the flip function are added in the full file at the end of the article. Go check it out!
### Calling the unittests
We can execute the file directly by adding the following lines to the end of the file
```python
if __name__ == '__main__':
    # Execute all tests in this file if the file is called directly from the commandline
    unittest.main()
```
Here, the line `if __name__ =='__main__':` serves as an execution guard: the condition evaluates to `true` if we call the file directly as `python tests.py` from the terminal. If it is imported as `import tests` in another file, nothing is executed.

The second option is to call `python -m unittest` in the directory where the tests are located.

If everything works correctly, you should get the following output upon executing the tests either of the two ways
```
..
----------------------------------------------------------------------
Ran 2 tests in 0.011s

OK
```
The two dots in the first line signify two tests that finish successfully. In case the test throws an error or the test fails, the dots will be substituted with `E` or `F`, respectively.

### The full file
Finally, here is the full file `tests.py` for copy-pasting (including a ton of comments).
```python
import unittest    # Import the testing framework
import numpy as np # Import numpy
import foo         # Import our file to be tested (foo.py)

# You can execute all tests in a folder with python -m unittest
# Otherwise, you can call this file directly and use the "__main__" block to execute the tests.

# For more information: https://docs.python.org/3/library/unittest.html

class TestMethods(unittest.TestCase):
    # A TestCase provides the framework for multiple tests.
    # A member function that starts with test* will be exectuted as a test.

    def setUp(self):
        # This setup is run before each test in the TestCase.
        # You can store data in the class (via self) that you need in multiple test functions.
        # This makes the functions a bit leaner.
        self.arr = np.array([0,1,2,3,4])
    
    def test_add_4(self):
        # Test foo.add_4
        for i in range(100):
            rnd = np.random.rand()
            val = foo.add_4(rnd)
            ref = rnd+4
            self.assertAlmostEqual(val,ref)

    def test_flip(self):
        # Test foo.flip_array
        val = foo.flip_array(self.arr)
        ref = np.array([4,3,2,1,0])
        self.assertTrue(np.allclose(val,ref))

if __name__ == '__main__':
    # Execute all tests in this file if the file is called directly from the commandline
    unittest.main()
```
## Other frameworks
`unittest` is not the only testing framework for Python, it is just the one that comes with [Python by default](https://docs.python.org/3/library/unittest.html). There are others, among them [`pytest`](https://docs.pytest.org/en/7.4.x/). In case you need more than `unittest` can have a look into an introduction to `pytest` [here](https://machinelearningmastery.com/a-gentle-introduction-to-unit-testing-in-python/).