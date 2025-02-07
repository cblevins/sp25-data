---
title: Working With Text in Python
---

## Overview

Today we'll be working with a single text: a narrative dictated by [Venture Smith](https://en.wikipedia.org/wiki/Venture_Smith), a successful businessman and formerly enslaved man in colonial-era New England. The narrative, _A Narrative of the Life and Adventures of Venture, a Native of Africa: But Resident above Sixty Years in the United States of America, Related by Himself_, is available in several formats online but for the purposes of today I've put it into the primary kind of file you will want to use when working with textual data in Python: a text file (ending in `.txt`).

## Get Updates

⚠️ ⚠️ ⚠️ Before starting any new work in this class, you always want to check for any updates from your instructor's `sp25-data-materials` repository.
{: .notice--warning}

- Open GitHub Desktop and select your course repository
- Make sure it says: `Current Branch: main` (ie. you're on the main branch)
- Click `Fetch origin` to check for any changes
- Go to Branch → `Merge into current branch` → select `upstream/main` and click `Create a merge commit` if there are updates
- Click `Pull origin` if it's available (if not, you're up to date!)
- Click `Push origin` to sync everything up

## Get Started in Jupyter Labs

- Open Anaconda Navigator, launch Jupyter Labs, and navigate to the `week-03` folder in `yourlastname-sp25-data-materials`
- Create a new Jupyter Notebook and name it: `yourlastname-working-with-text.ipynb`.

## Opening, Reading, and Writing Text Files

- Open up the `venture-smith.txt` text file in Jupyter Labs by double-clicking on the file in the left pane. This is how you, as a human reader, might read the contents of the file.
- Similarly, Python requires a two-step process to first open a file and then read its contents:
  - Add a code cell to `open` and `read` the file ([Walsh instructions](https://melaniewalsh.github.io/Intro-Cultural-Analytics/02-Python/07-Files-Character-Encoding.html)).
  - Assign the contents of the opened file to the variable `smith`
- Let's say we wanted to create a back-up copy of the file just in case. Follow the instructions in [the Walsh tutorial](https://melaniewalsh.github.io/Intro-Cultural-Analytics/02-Python/07-Files-Character-Encoding.html) to `write` a new file that copies the contents of your newly created `smith` variable into a new file named `venture-smith-copy.txt`

### Common String Methods in Python

- In a new code cell, add two lines of code. In the first line, just run your new variable `smith` to display its contents. In the second line, use `print()` to display its contents. What is the difference between these two?
- Use `index()` function to show the first character (letter) of Smith's narrative. It should show: `'A'`.
- Use `slice()` to show the first 100 characters (letters) of Smith's narrative. It should show: `'A NARRATIVE OF THE LIFE AND ADVENTURES\n\nOF VENTURE, A NATIVE OF AFRICA,\n\nBut resident above sixty ye'`
- Let's just isolate the title of Smith's narrative. This is comprised of the first 158 characters. Make a new variable called `smith_title` and assign it the first 158 characters of the text file (since Python starts counting at 0, this means we want to use `smith[0:157]`).
- Use [`string.title()`](<https://melaniewalsh.github.io/Intro-Cultural-Analytics/02-Python/06-String-Methods.html#:~:text=uppercase-,string.title(),makes%20the%20string%20titlecase,-string>) to reformat the title of Smith's narrative by making the first letter of each word capitalized.
  - Hint: the `string` in this example is your new variable `smith_title`.

## Analyzing Lines

- Notice how your main variable `smith` contains newline characters (`\n`). This is a "hidden" character contained in text files that tells a text editor to show the following text as starting on a new line (like hitting Enter or Return in a Word document).
  - Use [`string.split('delim')`](https://melaniewalsh.github.io/Intro-Cultural-Analytics/02-Python/06-String-Methods.html#:~:text=code%20here-,Split%20Strings%20By%20a%20Delimiter,Explanation,-string.split) to "split" up Smith's narrative into separate lines.
  - What would you use in place of `string.` and `delim` to do this?
  - Assign this new collection of separate lines to a new variable called `smith_lines` (this will create something called a "list" in Python)
- Check and see what's in your new variable by using the following code (don't worry if you don't understand it):

```python
for line in smith_lines:
  print(line)
```

- The [`len()`](https://www.w3schools.com/python/ref_func_len.asp) function tells you how long something is. In this case, we've created a variable called `smith_lines` containing a list of all the lines from Smith's narrative. Use `len()` and `smith_lines` to show the length of Smith's narrative in terms of the number of lines.

## Counting Words

As you saw in the Walsh tutorial [Anatomy of a Python Script](https://melaniewalsh.github.io/Intro-Cultural-Analytics/02-Python/03-Anatomy-Python-Script.html), one of the basic forms of text analysis you can do - and yet is central to more sophisticated forms of analysis - is to **count words.** Today we're going to count words in Venture Smith's narrative.

To do so, we're going to follow an age-old practice amongst coders: borrow other people's code and use it ourselves. Melanie Walsh provides precisely such a chunk of code in her tutorial to count words. See if you can copy and paste the below code (use the copy button) into your Jupyter Notebook and then edit it so that it is counting **the 20-most frequent words in Venture Smith's narrative.**

Here is Walsh's description of the code:

> Below is a chunk of Python code. These lines, when put together, do something simple yet important. They count and display the most frequent words in a text file. The example below specifically counts and displays the 40 most frequent words in Charlotte Perkins Gilman’s short story “The Yellow Wallpaper” (1892).

```python
import re
from collections import Counter

def split_into_words(any_chunk_of_text):
    lowercase_text = any_chunk_of_text.lower()
    split_words = re.split("\W+", lowercase_text)
    return split_words

filepath_of_text = "../texts/literature/The-Yellow-Wallpaper_Charlotte-Perkins-Gilman.txt"
number_of_desired_words = 40

stopwords = ['i', 'me', 'my', 'myself', 'we', 'our', 'ours', 'ourselves', 'you', 'your', 'yours',
 'yourself', 'yourselves', 'he', 'him', 'his', 'himself', 'she', 'her', 'hers',
 'herself', 'it', 'its', 'itself', 'they', 'them', 'their', 'theirs', 'themselves',
 'what', 'which', 'who', 'whom', 'this', 'that', 'these', 'those', 'am', 'is', 'are',
 'was', 'were', 'be', 'been', 'being', 'have', 'has', 'had', 'having', 'do', 'does',
 'did', 'doing', 'a', 'an', 'the', 'and', 'but', 'if', 'or', 'because', 'as', 'until',
 'while', 'of', 'at', 'by', 'for', 'with', 'about', 'against', 'between', 'into',
 'through', 'during', 'before', 'after', 'above', 'below', 'to', 'from', 'up', 'down',
 'in', 'out', 'on', 'off', 'over', 'under', 'again', 'further', 'then', 'once', 'here',
 'there', 'when', 'where', 'why', 'how', 'all', 'any', 'both', 'each', 'few', 'more',
 'most', 'other', 'some', 'such', 'no', 'nor', 'not', 'only', 'own', 'same', 'so',
 'than', 'too', 'very', 's', 't', 'can', 'will', 'just', 'don', 'should', 'now', 've', 'll', 'amp']

full_text = open(filepath_of_text, encoding="utf-8").read()

all_the_words = split_into_words(full_text)
meaningful_words = [word for word in all_the_words if word not in stopwords]
meaningful_words_tally = Counter(meaningful_words)
most_frequent_meaningful_words = meaningful_words_tally.most_common(number_of_desired_words)

most_frequent_meaningful_words
```

## Bonus Practice

- Use `string.split()`, `index()`, and `len()` to:
  - Print **the 200th word** in Smith's narrative
  - Print the length of Smith's narrative measured by **number of total words**.
- Use `string.split()` to break Smith's narrative apart into separate chapters and then `len()` to calculate how long Chapter II is based on the **number of characters** in that chapter.
