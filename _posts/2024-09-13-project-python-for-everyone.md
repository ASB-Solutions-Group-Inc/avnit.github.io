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

## The learning path

| Module | What it covers |
| :--- | :--- |
| **Class 1 — Fundamentals** | Variables and dynamic typing, strings, conditionals, loops, sequences (lists/tuples), user input |
| **Class 2 — Functions & Modules** | Function definition and recursion, scope and namespaces, string methods, writing and importing modules, named tuples |
| **Class 3 — Object-Oriented Programming** | Classes, inheritance and polymorphism, operator overloading (a custom `Vector` class), method overriding — plus detours into bubble sort and socket programming |
| **Class 4 — Data Science Foundations** | NumPy arrays and universal functions, Pandas DataFrames, slicing, SQLite, building web APIs with FastAPI, Jupyter notebooks (including a Lorenz-attractor demo) |
| **Class 5 — Advanced Concepts** | Exception handling, file operations, a bank-account OOP project, custom math classes, matplotlib basics |
| **Class 6 — Visualization & Finance** | Financial functions, portfolio analysis, advanced plotting and styles, working with Excel files |
| **Financial Analytics** | Pulling live market data with `yfinance`, data pipelines, and portfolio datasets |

## How it's built

Each class folder contains standalone scripts you can run directly (`python Class-1/variables.py`), along with the PDF/PowerPoint slides used in the live sessions and homework with solutions. The stack covers the core teaching toolkit: **NumPy, Pandas, Matplotlib, yfinance, FastAPI, SQLite, and Jupyter**.

The repo also practices what it preaches — PEP 8 style, docstrings throughout, and GitHub Actions running pylint on every push. It's MIT-licensed, so anyone is welcome to learn from it or fork it for their own class.

**Language:** Python / Jupyter Notebook
**Source code:** [github.com/avnit/Python-for-everyone](https://github.com/avnit/Python-for-everyone)
