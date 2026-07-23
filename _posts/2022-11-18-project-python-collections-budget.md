---
layout: post
title: "Python Collections Budget"
subtitle: "Learning Python collections by analyzing spending data"
gh-repo: avnit/python-collections-budget
gh-badge: [star, fork]
tags: [projects, python, learning]
comments: false
---

Python Collections Budget is a guided exercise that processes real spending data into different Python collection types, then uses them to graph spending categories and budget outcomes. This is my fork of the project, kept in my account as a hands-on way to get fluent with Python's collections.

## The concepts

The project is built around the standard library's data structures. You read a CSV of expenses into `Expense` objects, then reach for the right collection for each question: a `Counter` to tally purchases by category and pull the top five with `most_common()`, `zip()` to split a dictionary into parallel lists, and matplotlib to plot the result as a bar chart. It's a nice, concrete way to see why the collection you choose shapes how easy the analysis becomes.

## How to use it

Each module is verifiable with pytest, so you can work through it test-first and check your results as you go.

```bash
python -m venv venv
source venv/bin/activate
python -m pip install -r requirements.txt
pytest -k "module1" -s
```

**Language:** Python
**Source code:** [github.com/avnit/python-collections-budget](https://github.com/avnit/python-collections-budget)
