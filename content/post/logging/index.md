---
title: Logging -- boring but really useful
subtitle: 
summary: "Some parts of a program's code are the unsung heroes. Nobody really talks about the logging infrastructure in a program. But when something goes wrong a proper log file might be all you need."
authors:
  - admin
tags: ['Tools','Python']
categories: []
projects: []
draft: false
featured: false
share: false
date: '2024-08-16T00:00:00Z'
lastMod: '2023-08-16T00:00:00Z'
image:
  caption: 'generated by DALL-E'
  focal_point: ''
  preview_only: true
---  
You start a command line program and you don't get any feedback, just a blinking prompt.
Not the best of feelings... Is the program actually doing something or is it just idling?

The easiest way to fix that is a bit of feedback on the command line. While `print` statements generally do the job, it would be nice to also attach some more information, like the severity of the messages or even to be able to filter for different messages.
This is exactly the job of logging.

# TL;DR
Logging is a structured way to output information from your program to the commandline and to the user.
The `logging` module in Python is a very convenient way to set up up a logging infrastructure in Python.

# Not all output is created equal
Before we dive into the Python part of this tutorial, we have to make a quick detour via the Linux command line. 
After all, that is where the output will be visible.
The Linux command line distinguishes by default between two output streams: `stdout` and `stderr`, ''standard out'' and ''standard error''.
As the names suggest, the first one is for general information, the second one is meant for errors.

On the command line, we usually do not see much of a difference between the two streams.
The difference only becomes apparent if we write the output of a program to file.
The command
```
foo > bar.txt
```
writes the output of the program `foo` to the file `bar.txt`.
However, not all the output, only `stdout` is written to file by default.
If `foo` throws an error, it will still be displayed on the command line.

If you really want to move all output of a program to a file, i.e. `stdout` and `stderr`, you have to use
```
foo &> bar.txt
```
The operator `&>` writes both output streams to the file.

If you want to play with redirecting streams, you can use the following bash script
```bash
#!/bin/bash
set -eu
echo "Start" >&2
for i in $(seq 10)
do
    echo "$i$
done

echo "End" >&2
```
The messages "Start" and "End" are written to `stderr`. 
If you use `> bar.txt`, only numbers appear in the file.
The messages "Start" and "End" are displayed on the command line.
Only with `&> bar.txt`, you see all messages in the file.

# Managing output streams in Python
When we are logging in Python, we can decide which messages are sent to `stdout` and which messages are sent to `stdout`.

Messages in the logging package are classified in five levels `DEBUG`,`INFO`,`WARNING`, `ERROR`, and `CRITICAL`.
General information is usually logged as `INFO`, while additional information for developers can be logged as `DEBUG` to facilitate the search for bugs.
Starting from `WARNING`, we will send the information to `stderr` instead of `stdout`.

Let's set up the `logging` package:

1. We import the package with `import logging`
2. We set up the handlers for the `stdout` and `stderr`  
```python
h_stdout = logging.StreamHandler(stream=sys.stdout)
h_stderr = logging.StreamHandler(stream=sys.stderr)
```
3. Since we do not want to add all messages to `stderr`, we add a filter. If we only add a single filter, you will see error messages twice, once in `stdout` and once in `stderr`. 
If you want to avoid that, you also have to set a filter for the `h_stdout` handler.
```python
h_stderr.addFilter(lambda record: record.levelno >= logging.WARNING)
```

4. Finally, we have to tell the `logging` package about our configuration.
Here, I added for convenience a `FileHandler` which writes the log automatically to file. The file name can be chosen arbitrarily, here we assume that the program gets to input parameters `a` and `b` that we use to name the file.

``` python
logging.basicConfig(
        level = args.level.upper(),
        format = "%(asctime)s [%(levelname)s] %(message)s",
        handlers = [
            logging.FileHandler(f"main_{a:.2f}_{b:.2f}.log"),
            h_stdout,
            h_stderr
        ]
    )
```


# The full code
The snippets above are taken from a full example that you can find here.
This script just computes the addition of two numbers in a function `add_numbers` (with a lot of logging surrounding it).

```python
import numpy as np
import logging
import sys,os

def add_numbers(a,b):
    """Dummy function to add two numbers

    Args:
        a (float): First Number
        b (float): Second Number

    Returns:
        Float: Addition of the two numbers
    """
    return a+b

def main(args):
    # Set up the logger
    h_stdout = logging.StreamHandler(stream=sys.stdout)
    h_stderr = logging.StreamHandler(stream=sys.stderr)
    h_stderr.addFilter(lambda record: record.levelno >= logging.WARNING)
    logging.basicConfig(
        level = args.level.upper(),
        format = "%(asctime)s [%(levelname)s] %(message)s",
        handlers = [
            logging.FileHandler(f"main_{a:.2f}_{b:.2f}.log"),
            h_stdout,
            h_stderr
        ]
    )
    
    #Start of main function
    # Let's print the initial parameters given via the command line as INFO level
    logging.info("=====================")
    logging.info(f"Parameter a: {a:.2f}")
    logging.info(f"Parameter b: {b:.2f}")
    logging.info("=====================")
    logging.debug(f"Starting computation with parameters {a} and {b}")
    c=add_numbers(a,b)
    logging.debug(f"End computation with parameters {a} and {b}")

    logging.info(f"Result of computation: {c:.2f}")

# This is an execution guard.
# This parts only gets executed when you call the file directly via "python <....>" 
if __name__ == "__main__":
    main(2,3)
```
