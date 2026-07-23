---
layout: post
title: Python for Everyone
subtitle: "A hands-on Python course I teach — from first variables to financial analytics"
gh-repo: avnit/Python-for-everyone
gh-badge: [star, fork, follow]
tags: [projects, python, teaching, data-science, finance]
comments: false
---

**Python for Everyone** is the full curriculum for a Python course I teach, aimed at beginners and intermediate learners. It takes students from their first variable all the way to real financial analysis, through six progressive class modules plus an advanced analytics track — every concept backed by runnable code, slides, and homework.

## The learning path at a glance

| Module | What it covers |
| :--- | :--- |
| **Class 1 — Fundamentals** | Variables and dynamic typing, strings, conditionals, loops, sequences (lists/tuples), user input |
| **Class 2 — Functions & Modules** | Function definition and recursion, scope and namespaces, string methods, writing and importing modules, named tuples |
| **Class 3 — Object-Oriented Programming** | Classes, inheritance and polymorphism, operator overloading (a custom `Vector` class), method overriding — plus detours into bubble sort and socket programming |
| **Class 4 — Data Science Foundations** | NumPy arrays and universal functions, Pandas DataFrames, slicing, SQLite, building web APIs with FastAPI, Jupyter notebooks (including a Lorenz-attractor demo) |
| **Class 5 — Advanced Concepts** | Exception handling, file operations, a bank-account OOP project, custom math classes, matplotlib basics |
| **Class 6 — Visualization & Finance** | Financial functions, portfolio analysis, advanced plotting and styles, working with Excel files |
| **Financial Analytics** | Pulling live market data with `yfinance`, data pipelines, and portfolio datasets |

## Inside each module

### Class 1: Python Fundamentals — `Class-1/`

- **Variables and Data Types** (`variables.py`) — Python's dynamic typing, numeric types, strings, and complex numbers
- **Conditional Statements** (`condition-if.py`) — basic if-else logic and control flow
- **Loops** (`for-loop.py`) — iteration with for and while loops
- **Sequences** (`Sequences.py`) — lists, tuples, and sequence operations
- **String Operations** (`strings.py`) — string manipulation and formatting
- **User Input** (`user-input.py`) — interactive programs with user input
- **Assignment Operators** (`Assignment-operator.py`) — assignment and arithmetic operators

### Class 2: Functions and Modules — `Class-2/`

- **Function Basics** (`functions.py`) — definition, parameters, return values, and recursion
- **Scope and Namespaces** (`scope.py`, `global-scope.py`) — variable scope and global/local variables
- **String Functions** (`String-functions.py`) — built-in string methods and operations
- **Modules** (`modules.py`) — creating and importing Python modules
- **Named Tuples** (`named-tuple.py`) — advanced data structures
- **Loop Functions** (`loop-functions.py`) — functional programming with loops

### Class 3: Object-Oriented Programming — `Class-3/`

- **Classes and Objects** (`Classes.py`) — basic OOP concepts, inheritance, and polymorphism
- **Operator Overloading** (`usingOperatorOverload.py`, `Vector.py`) — custom operators for classes
- **Class Override** (`ClassOverride.py`) — method overriding and inheritance
- **Sorting Algorithms** (`bubble-sort.py`) — implementation of sorting algorithms
- **Web Development** (`build-webpage.py`) — basic web page generation
- **Network Programming** (`my_socket_server.py`) — socket programming basics

### Class 4: Data Science Foundations — `Class-4/`

- **NumPy Arrays** (`numpy-array-setting.py`, `numpy-details.py`) — numerical computing with NumPy
- **NumPy Functions** (`numpy-functions.py`, `numpy-universal-functions.py`) — advanced NumPy operations
- **Pandas DataFrames** (`pandas-dataframe-load.py`, `pandas-dataframe.py`) — data manipulation with Pandas
- **Data Slicing** (`slicing-array.py`) — array and DataFrame slicing techniques
- **Web APIs** (`complex-fastapi.py`, `fastcgi.py`) — building web APIs with FastAPI
- **Database Operations** (`sqlite.ipynb`) — SQLite database integration
- **Jupyter Notebooks** (`Intro.ipynb`, `Lorenz.ipynb`) — interactive data analysis

### Class 5: Advanced Python Concepts — `Class-5/`

- **Exception Handling** (`exception-handle.py`, `try-except.py`) — error handling and debugging
- **File Operations** (`file-operation.py`) — reading and writing files
- **Bank Account System** (`bankaccount.py`) — practical OOP application
- **Mathematical Operations** (`fraction.py`, `cube.py`) — custom mathematical classes
- **Data Analysis** (`numpy-second-section.py`, `pandas-dataframe.py`) — advanced data processing
- **Visualization** (`plots.py`) — basic plotting with matplotlib
- **Homework Solutions** (`homework.py`, `hw2.py`) — practice exercises

### Class 6: Data Visualization and Financial Analysis — `Class-6/`

- **Financial Functions** (`financial_functions.py`) — financial calculations and metrics
- **Portfolio Analysis** (`funds.py`, `keg.py`) — investment portfolio management
- **Data Visualization** (`plot.py`, `plot-style.py`) — advanced plotting techniques
- **Matplotlib Integration** — comprehensive plotting examples
- **Excel Integration** (`apple.xlsx`, `myportfolio.xlsx`) — working with Excel files

### Financial Analytics: Advanced Applications — `Financial-Analytics/`

- **Data Acquisition** (`scripts/1_financial_data.py`) — downloading financial data with yfinance
- **Image Processing** (`scripts/convertImagetoCode.py`) — converting images to code
- **Subprocess Management** — system integration scripts
- **Data Storage** (`data/`) — financial datasets and portfolio data

## How it's built

Each class folder contains standalone scripts you can run directly (`python Class-1/variables.py`), along with the PDF/PowerPoint slides used in the live sessions and homework with solutions. The stack covers the core teaching toolkit: **NumPy, Pandas, Matplotlib, yfinance, FastAPI, SQLite, and Jupyter**.

The repo also practices what it preaches — PEP 8 style, docstrings throughout, and GitHub Actions running pylint on every push. It's MIT-licensed, so anyone is welcome to learn from it or fork it for their own class.

**Language:** Python / Jupyter Notebook
**Source code:** [github.com/avnit/Python-for-everyone](https://github.com/avnit/Python-for-everyone)
