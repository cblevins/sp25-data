---
title: Lists and Loops Practice Instructor Version
---

# Lists, Dictionaries, and Functions - Instructor Guide

This is the instructor version of the exercise with completed code examples and explanations.

## Overview

Today's exercise is going to give students practice with understanding and working with lists, for loops, dictionaries, and functions. Our goals:

- Take a list of history faculty members at CU Denver
- Use their full names to generate an email address for each of them
- Create a dictionary that stores their name and email address

## Getting the Data

The first step is to get the data. To give students some practice with navigating folders and opening files, I've put a list of rostered faculty members from the CU Denver history department in a text file called `history-faculty.txt` inside a sub-folder named `history-department`. We're going to import the `pathlib` library to help us:

```python
# Import the pathlib library
from pathlib import Path
```

Next, we'll use the `pathlib` library to navigate to our folder and give us a list of the files inside it ending in `.txt`.

```python
# Look inside a directory and list all the text files in it
files_list = list(Path('history-department').glob('*.txt'))
for file in files_list:
    print(file)

# Expected output:
# history-department/history-faculty.txt
```

We just want the file `history-faculty.txt`. Let's open the file and take a look:

```python
faculty_file = open('history-department/history-faculty.txt', 'r').read()
faculty_file

# Expected output (with \n characters):
# 'Christopher Agee\nCameron Blevins\nRyan D. Crewe\nGabriel Finkelstein\nXiaofei Gao\nRachel Gross\nPeter A. Kopp\nMarjorie Levine-Clark\nBrandon Mills\nDale J. Stahl\nChristine Sundberg\nSteven M. Vose\nWilliam Wagner\nGreg Whitesides\nKariann Akemi Yokota'
```

Notice how it contains `\n` characters - those hidden characters indicating a new line. If we were to use the print() function, it would look more legible and indicate that there is one faculty member's name on each line.

```python
print(faculty_file)

# Expected output:
# Christopher Agee
# Cameron Blevins
# Ryan D. Crewe
# Gabriel Finkelstein
# Xiaofei Gao
# Rachel Gross
# Peter A. Kopp
# Marjorie Levine-Clark
# Brandon Mills
# Dale J. Stahl
# Christine Sundberg
# Steven M. Vose
# William Wagner
# Greg Whitesides
# Kariann Akemi Yokota
```

Now we want to create a new list called `faculty_list` in Python, with each item in the list corresponding to the name of a faculty member pulled from the `history-faculty.txt` file. To do so, we can use the `split()` function to create a list from this text file, splitting it up by each line (ie. on the newline or `\n` character).

```python
faculty_list = faculty_file.split('\n')
for item in faculty_list:
    print(item)

# Expected output:
# Christopher Agee
# Cameron Blevins
# Ryan D. Crewe
# Gabriel Finkelstein
# Xiaofei Gao
# Rachel Gross
# Peter A. Kopp
# Marjorie Levine-Clark
# Brandon Mills
# Dale J. Stahl
# Christine Sundberg
# Steven M. Vose
# William Wagner
# Greg Whitesides
# Kariann Akemi Yokota
```

## Understanding the Problem

Students should brainstorm steps to tackle the problem. Sample response:

- For each name in the faculty list:
  - Split the name into parts (first, middle, last)
  - Identify which part is the first name and which is the last name
  - Handle special cases (middle initials, hyphenated names)
  - Create an email format with first name + period + last name + @ucdenver.edu
  - Make everything lowercase
- Create a dictionary to store the information
  - Use the full name as the key
  - Use the generated email as the value
- Process the entire list using a loop

## Email Generation Function

### Describe the Problem

Students should break down the problem into steps. Sample response:

- Split the full name into separate parts using the space character
- Identify the first name (first part) and last name (last part)
- Handle middle initials by ignoring them
- Handle hyphenated last names by keeping the hyphen
- Convert all parts to lowercase
- Join the first and last names with a period
- Add "@ucdenver.edu" at the end
- Return the complete email address

### Define the Function

Students should create a function to generate email addresses:

```python
def generate_email(full_name):
    """
    Generates a UCDenver email address from a person's full name.
    Format: firstname.lastname@ucdenver.edu

    Parameters:
        full_name (str): The person's full name

    Returns:
        str: The generated email address
    """
    # Split the name into parts
    name_parts = full_name.split()

    # Get the first name (first part)
    first_name = name_parts[0]

    # Get the last name (last part)
    last_name = name_parts[-1]

    # Create the email address
    email = f"{first_name.lower()}.{last_name.lower()}@ucdenver.edu"

    return email
```

### Test the Function

Students should test the function with a sample name:

```python
test_name = "Ryan D. Crewe"
email = generate_email(test_name)
print(f"Name: {test_name}")
print(f"Email: {email}")

# Expected output:
# Name: Ryan D. Crewe
# Email: ryan.crewe@ucdenver.edu
```

## Building the Dictionary

Students should create a dictionary to store the faculty emails:

```python
# Create an empty dictionary
faculty_emails = {}

# Loop through the faculty list
for name in faculty_list:
    # Generate email for this faculty member
    email = generate_email(name)

    # Add to dictionary with name as key and email as value
    faculty_emails[name] = email

# Print the length of the dictionary
print(f"Created emails for {len(faculty_emails)} faculty members")

# Expected output:
# Created emails for 15 faculty members
```

### Test the Dictionary

Students should print the dictionary contents:

```python
# Print out the contents of the dictionary
for name, email in faculty_emails.items():
    print(f"{name}: {email}")

# Expected output:
# Christopher Agee: christopher.agee@ucdenver.edu
# Cameron Blevins: cameron.blevins@ucdenver.edu
# Ryan D. Crewe: ryan.crewe@ucdenver.edu
# Gabriel Finkelstein: gabriel.finkelstein@ucdenver.edu
# Xiaofei Gao: xiaofei.gao@ucdenver.edu
# Rachel Gross: rachel.gross@ucdenver.edu
# Peter A. Kopp: peter.kopp@ucdenver.edu
# Marjorie Levine-Clark: marjorie.levine-clark@ucdenver.edu
# Brandon Mills: brandon.mills@ucdenver.edu
# Dale J. Stahl: dale.stahl@ucdenver.edu
# Christine Sundberg: christine.sundberg@ucdenver.edu
# Steven M. Vose: steven.vose@ucdenver.edu
# William Wagner: william.wagner@ucdenver.edu
# Greg Whitesides: greg.whitesides@ucdenver.edu
# Kariann Akemi Yokota: kariann.yokota@ucdenver.edu
```

## Bonus (Optional)

For the bonus, students should process the student file and create more complex dictionaries:

```python
# Read the student file
student_file = open('history-department/history-students.txt', 'r').read()
student_list = student_file.split('\n')

# Create a dictionary for student emails
student_emails = {}
for name in student_list:
    # Generate email for this student
    email = generate_email(name)

    # Add to dictionary with name as key and email as value
    student_emails[name] = email

# Create a combined dictionary for both faculty and students
all_emails = {**faculty_emails, **student_emails}  # Python 3.5+ dictionary unpacking
print(f"Combined dictionary has {len(all_emails)} entries")

# Create a nested dictionary with additional information
detailed_directory = {}

# Add faculty to the detailed directory
for name in faculty_list:
    detailed_directory[name] = {
        "name": name,
        "email": generate_email(name),
        "status": "faculty"
    }

# Add students to the detailed directory
for name in student_list:
    detailed_directory[name] = {
        "name": name,
        "email": generate_email(name),
        "status": "student"
    }

# Print a sample from the detailed directory
for name, info in list(detailed_directory.items())[:5]:  # Just show first 5
    print(f"{name}:")
    for key, value in info.items():
        print(f"  {key}: {value}")
    print()

# Create a combined dictionary for both faculty and students
all_emails = {}
# Add faculty emails
for name, email in faculty_emails.items():
    all_emails[name] = email
# Add student emails
for name, email in student_emails.items():
    all_emails[name] = email
print(f"Combined dictionary has {len(all_emails)} entries")

# Expected output:
# Combined dictionary has 25 entries
#
# Christopher Agee:
#   name: Christopher Agee
#   email: christopher.agee@ucdenver.edu
#   status: faculty
#
# Cameron Blevins:
#   name: Cameron Blevins
#   email: cameron.blevins@ucdenver.edu
#   status: faculty
#
# ...etc...

```
