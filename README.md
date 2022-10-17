# PY Pull From Receipts

## Introduction
The intent of this project is to import and parse digital receipts in a variety of forms.
In the case of digital text receipts, the parsing process will be relatively straight forward: identify key information and extract.
In the case of digital receipts in PDF or image form, the parsing process may require use of optical character recognition (OCR) to extract information from such receipts. The goal of this project is to pull, parse and export this information to in a spreadsheet friendly format. Internally, the project may use JSON or some other schema for internal representation. As an additional feature, I plan to support the use of a categorization file which the program can use to auto categorize transactions. This feature is aimed at simplifying purchase habits and trends from retailers which offer a variety of goods.

## Dependencies
TBD: Likely: Python 3.7, ImageMagick.

## Components & Plan
Building up the base skeleton project first should capture most of the benefit this project brings.
By prioritizing receipts already in digital form first, it will be simpler to build the semantic parsing function rather than trying to tackle a complex case such as character recognition on scanned receipts.

I envision a handful of components to this program, in order of the data flow:

1. I/O module:
   This component will handle file I/O. It will take in digital text files and convert to sequences of strings, and it will take a data payload from output modules and write to file.
2. Semantic parser:
   The core component of this program. Planned to be written in Python. Goal is to take in sequentially read strings, from top to bottom, left to right, and assign semantic meaning to them. This should be capable of making sense of a variety of receipts, identifying store, purchase date, items purchased and prices.
3. Categorization module:
   This module will be left until last in initial development. The plan is for this to take in a user provided config file, from which higher level semantic grouping can be assigned to items based on item name, description, and or retailer.
4. Writer module:
   This component will convert the internally recognized and represented data into a standard format suitable for inclusion within a digital spreadsheet program. Optionally, it could be designed to take a reference spreadsheet in as a template for formatting.
   
### Example data

This repo will house example digital receipts in the *data/examples* folder. I will start with 3 types of receipts pulled from popular retailers, anonymized and truncated for simplicity. I will focus on the following retailers:

1. Home Depot
2. Costco
3. Amazon

Each of these retailers offers a digital receipt history tied to a purchasing account, each in a relatively unique format. This should provide sufficient diversity to build out the basic application in a way that can be easily generalized.