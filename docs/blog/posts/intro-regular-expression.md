---
date:
    created: 2025-04-13
readtime: 20
# authors:
#   - team
categories:
  - Python
tags:
  - regular expression
  - regex
  - quanitier
  - meta characters
  - special sequence characters
---

# Introduction to Regular Expressions
- Download PDF: [Introduction to Regular Expression](https://github.com/marslearnings/Python_Regular_Expressions/blob/main/pdf/Introduction_to_Regular_Expressions.pdf)
- Video Explanation:  [YOUTUBE](https://youtu.be/75G4GajQdgQ)

Regular expressions (regex) are patterns used to match character combinations in strings. These patterns can be simple characters or a combination of simple and special characters.

Examples:

- `/abc/` - A simple pattern matching the literal string "abc"
- `/ab*c/` - A pattern using special characters to match variations

## The Regular Expression Syntax

Regular expressions follow a specific syntax:

- In standard notation: `/pattern/`
- In Python: `r"pattern"`

When a pattern is applied to text, it returns the range where the pattern exists in the string.

## Literals or Simple Characters

Simple literals match the exact characters in the pattern.

Example:

- `/cat/` matches the string "cat" within text

## Meta Characters

Meta characters give regular expressions their power, allowing for more sophisticated matching.

### Special Characters

| Character | Description | Example | Match |
|-----------|-------------|---------|-------|
| \| | Either or | `cat\|hello` | Matches "cat" or "hello" |
| . | Any character (except newline) | `he..lo` | Matches characters between "e" and "l" |
| { } | Exactly specified number of occurrences | `he.{2}o` | Matches "hello" where there are exactly 2 characters between "e" and "o" |
| * | Zero or more occurrences | `he.*o` | Matches "hello", "hero", "helico", etc. |
| + | One or more occurrences | `he.+o` | Same as above but requires at least one character |
| ? | Zero or one occurrence | `he.?o` | Matches "heo" or "hero" |
| ( ) | Capture and group patterns | | |
| [ ] | A set of characters | `[a-z]` | Matches any lowercase letter |
| ^ | Starts with | `^hello` | Matches strings starting with "hello" |
| $ | Ends with | `world$` | Matches strings ending with "world" |
| \ | Signals a special sequence | `\d` | Matches any digit |

### Character Classes

Character classes allow you to define a set of characters where any single character from that set will match.

| Expression | Description |
|------------|-------------|
| `[cs]` | Matches either "c" or "s" (e.g., `/licen[cs]e/` matches "licence" or "license") |
| `[0-9]` | Matches any digit from 0 to 9 |
| `[a-z]` | Matches any lowercase letter |
| `[A-Z]` | Matches any uppercase letter |
| `[0-9a-zA-Z]` | Matches any alphanumeric character |
| `[^0-9]` | Matches any character that is NOT a digit |
| `[^a-z]` | Matches any character that is NOT a lowercase letter |

### Quantifiers

Quantifiers define how many times a character, metacharacter, or character set can be repeated.

| Symbol | Name | Meaning |
|--------|------|---------|
| ? | Question Mark | 0 or 1 repetition |
| * | Asterisk | Zero or more times |
| + | Plus sign | One or more times |
| {n,m} | Curly braces | Between n and m times |

Examples:

- `/hello*/` matches "hell", "hello", "helloo", "hellooo", etc.
- `/hello+/` matches "hello", "helloo", "hellooo", etc. (but not "hell")
- `/hello?/` matches only "hell" or "hello"
- `/hello{2,5}/` matches "helloo", "hellooo", "helloooo", "hellooooo"

## Special Sequence Characters

### Pre-defined Characters

| Character | Description | Equivalent |
|-----------|-------------|------------|
| \w | Word characters (letters, digits, underscore) | `[a-zA-Z0-9_]` |
| \W | NOT word characters | `[^a-zA-Z0-9_]` |
| \d | Digits | `[0-9]` |
| \D | NOT digits | `[^0-9]` |
| \s | Whitespace characters | `[ \t\n\r\f\v]` |
| \S | NOT whitespace characters | `[^ \t\n\r\f\v]` |

## Boundary Characters

Boundary matchers identify specific positions within the input text.

| Matcher | Description |
|---------|-------------|
| ^ | Matches at the beginning of a line |
| $ | Matches at the end of a line |
| \b | Matches a word boundary (beginning or end of word) |
| \B | Matches anything that is NOT a word boundary |
| \A | Matches the beginning of the input |
| \Z | Matches the end of the input |

## Practice Exercises

### Excerise 1: Basic Pattern Matching

Consider this example string:
```
The quick brown fox jumps over the lazy dog. This is outside (this is inside)
```

| Question | Answer |
|----------|--------|
| Match the string "fox" and provide its range | 16-19 |
| How many times does "is" appear in the string? | 4 |
| Match the pattern "(this is inside)" and provide its range | 61-77 |

### Excerise 2: Using OR Operator (pipe)

For the string:
```
The sun rises in the east and sets in the west. Birds sing in the morning or evening.
```

| Question | Pattern |
|----------|---------|
| Match either "sun" or "moon" | `sun|moon` |
| Match either "east" or "west" | `east|west` |
| Match either "morning" or "evening" | `morning|evening` |
| Match either "rises", "sets", or "sing" | `rises|sets|sing` |
| Match either "The" or "Birds" | `The|Birds` |

### Excerise 3: Character Set, dot(.)

For this data:
```
Contact Information:
John Doe - john.doe@example.com - (555) 123-4567
Mary Smith - mary_smith@email.net - 555.987.6543
Tom Johnson - tom-johnson@company.org - (555)246-8910
Sarah Brown - sarah@brown.co.uk - +1-555-369-7412
Mike Wilson - mike.wilson@subdomain.example.edu - 555 741 0258
```

| Question | Pattern |
|----------|---------|
| Match any single vowel | `[aeiou]` |
| Match either "John" or "Tom" | `John|Tom` |
| Match any character that is NOT a digit | `[^0-9]` |
| Match either "com" or "net" in email domains | `com|net` |
| Match any single digit in phone numbers | `[0-9]` |
| Match any character between 'T' and 'm' in "Tom" | `T.m` |
| Match any single uppercase letter | `[A-Z]` |
| Match any character that is not a letter or number | `[^0-9a-zA-Z]` |


### Excerise 4: Quantiers

Consider the below example string and Use the "The Curious Case of the Missing Code" text to answer the following questions. 

```
The Curious Case of the Missing Code

John_Smith123 was panicking. It was 9:30 AM on April 15, 2025, and he had just realized that the crucial code files for Project-X2021 were missing from his laptop. Yesterday at 17:45, everything had been fine when he left the office at 42 Maple Street, Suite #301.

He quickly sent an email to his boss (anna.director@techcorp.com) and his team members (dev.team@techcorp.com):

Subject: URGENT - Missing Project Files
Body: Team, I can't locate the following files:
- main_v3.2.py
- config_prod.json
- api_keys.txt (IP: 192.168.1.100)

I've checked my backups from 2023-12-01 through 2025-03-15 but found nothing. Has anyone committed changes to the repository at http://git.techcorp.com/projects/x2021? My phone number is (555) 123-4567 if you need to reach me urgently. The project deadline is in 72 hours!

Lisa responded first at 9:42 AM: "I saved a copy at C:\Projects\Backup\X2021-backup.zip. The password is XB21-9$f5. You can also check with Mark who was working late yesterday."

John sighed with relief. Crisis averted! Now he needed to update the project documentation with proper file paths like /usr/local/bin/project-x/ for Linux users and C:\Program Files\Project-X\ for Windows users.

He made a note to call Lisa later at +1-555-987-6543 to thank her properly.
```
Create regular expressions that match exactly what's requested (nothing more, nothing less).

> Basic Character Sets

1. Create a pattern that matches all instances of dates in the format YYYY-MM-DD.
2. Write a regex that finds all alphanumeric identifiers that contain both letters and numbers (like "John_Smith123" or "Project-X2021").
3. Match all times in the HH:MM AM/PM format.

> Predefined Character Classes

4. Create a pattern using \d and \w to extract all phone numbers in the format (555) 123-4567 or +1-555-987-6543.
5. Write a regex using \s and \S to find all file paths (both Windows and Linux style).
6. Develop a pattern using \w, \d, and \s to match all file names with version numbers (like "main_v3.2.py").

> Metacharacters and Alternation

7. Use the pipe operator (|) to match either email addresses or web URLs.
8. Create a pattern with the dot (.) metacharacter to find all text within parentheses.
9. Write a regex that matches IP addresses like 192.168.1.100.

> Combined Challenge

10. Create a comprehensive pattern that extracts all forms of contact information (emails and phone numbers) from the text.


**Solution**

1. Pattern to match dates in YYYY-MM-DD format:
   ```
   \d{4}-\d{2}-\d{2}
   ```
   Matches: "2023-12-01", "2025-03-15"

2. Pattern for alphanumeric identifiers with both letters and numbers:
   ```
   [A-Za-z][A-Za-z0-9_]*\d+[A-Za-z0-9_]*
   ```
   Matches: "John_Smith123", "Project-X2021", "XB21-9$f5" (part of it)

3. Pattern for times in HH:MM AM/PM format:
   ```
   \d{1,2}:\d{2}\sAM|\d{1,2}:\d{2}\sPM
   ```
   Matches: "9:30 AM", "9:42 AM"

4. Pattern for phone numbers using \d and \w:
   ```
   \(\d{3}\)\s\d{3}-\d{4}|\+\d-\d{3}-\d{3}-\d{4}
   ```
   Matches: "(555) 123-4567", "+1-555-987-6543"

5. Pattern for file paths using \s and \S:
   ```
   [A-Z]:\\[^\s]+|/\S+/
   ```
   Matches: "C:\Projects\Backup\X2021-backup.zip", "C:\Program Files\Project-X\", "/usr/local/bin/project-x/"

6. Pattern for filenames with version numbers using \w, \d, and \s:
   ```
   \w+_v\d+\.\d+\.\w+
   ```
   Matches: "main_v3.2.py"

7. Pattern for email addresses or web URLs using pipe operator:**
   ```
   [a-zA-Z0-9_.]+@[a-zA-Z0-9_.]+\.[a-z]+|http://[^\s]+
   ```
   Matches: "anna.director@techcorp.com", "dev.team@techcorp.com", "http://git.techcorp.com/projects/x2021"

8. Pattern with dot metacharacter to find text in parentheses:
   ```
   \(.*?\)
   ```
   Matches: "(555) 123-4567", "(IP: 192.168.1.100)"

9. Pattern for IP addresses:
   ```
   \d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3}
   ```
   Matches: "192.168.1.100"

10. Comprehensive pattern for contact information:
    ```
    [a-zA-Z0-9_.]+@[a-zA-Z0-9_.]+\.[a-z]+|\(\d{3}\)\s\d{3}-\d{4}|\+\d-\d{3}-\d{3}-\d{4}
    ```
    Matches all email addresses and phone numbers in the text

### Excerise 6 - Boundary Matchers 
These questions are based on the following example string:

```
Hello world! This is line one.
World, hello! This is line two.
HelloWorld is a single word.
The word "hello" appears in quotes.
This line ends with hello
hello starts this line and world ends it with world
com.example.domain is a domain name
user@example.com is an email address.
2023-05-15 is a date format.
The final line ends the entire text.
```

**Questions on ^ (Caret) Boundary**

1. Write a regex pattern that matches any line beginning with the word "Hello".
2. Write a regex pattern that matches any line beginning with either "Hello" or "hello".
3. How many lines in the example string start with a capital letter?

**Questions on $ (Dollar) Boundary**

4. Write a regex pattern that matches any line ending with the word "hello".
5. How many lines in the example string end with a period (dot)?
6. Write a regex pattern that matches any line ending with the exact word "world".

**Questions on \b (Word Boundary)**

7. Write a regex pattern that matches the standalone word "hello" (case-insensitive) in the example text.
8. How many times does the standalone word "world" (lowercase only) appear in the example text?
9. Write a regex pattern that matches the word "is" only when it appears as a complete word.

**Questions on \B (Non-word Boundary)**

10. Write a regex pattern that matches "World" only when it's part of another word without word boundaries.
11. In the example text, what word contains "World" without word boundaries on either side?
12. Write a regex that matches "example" when it's part of a larger word or token.

**Questions on \A (Start of String)**

13. What single word would a regex pattern \AHello match in our example text?
14. Write a regex that matches the first 5 characters of the entire example text.
15. How does the pattern \AThe perform on our example text?

**Questions on  \Z (End of String)**

16. Write a regex pattern that matches the last sentence of the entire example text.
17. What's the last word in the entire example text that would be matched by \w+\.\Z?
18. Write a regex that matches the last 10 characters of the entire example text.


**Solution**


1. Write a regex pattern that matches any line beginning with the word "Hello".

```
^Hello.+
```
2. Write a regex pattern that matches any line beginning with either "Hello" or "hello".

```
^[Hh]ello.+
```
3. How many lines in the example string start with a capital letter ?

```
^[A-Z].+
```
4. Write a regex pattern that matches any line ending with the word "hello".

```
.+hello$
```
5. How many lines in the example string end with a period (dot)?

```
.+\.$
```
6. Write a regex pattern that matches any line ending with the exact word "world".

```
.+\bworld\b$
```
7. Write a regex pattern that matches the standalone word "hello" (case-insensitive) in the example text.

```
\b[Hh]ello\b
```
8. How many times does the standalone word "world" (lowercase only) appear in the example text?

```
\bworld\b
```
9. Write a regex pattern that matches the word "is" only when it appears as a complete word.

```
\bis\b

```
10. Write a regex pattern that matches "World" only when it's part of another word without word boundaries.

```
\BWorld\B\
```
11. In the example text, what word contains "World" without word boundaries on either side?

```
\w+.+\BWorld\B\w+.+
```

12. Write a regex that matches "example" when it's part of a larger word or token.

```
\Bexample\B
```
13.  What single word would a regex pattern \AHello match in our example text?

It matches word Hello in entire string

14.  Write a regex that matches the first 5 characters of the entire example text.

```
\A.{5}
```
15.  How does the pattern \AThe perform on our example text?

No pattern is identified

16.Write a regex pattern that matches the last sentence of the entire example text.

```
.+\Z
```

17.What's the last word in the entire example text that would be matched by \w+\.\Z?

```
text.
```

18.Write a regex that matches the last 10 characters of the entire example text.

```
.{10}\Z
```



## Warning

The dot (.) is a very powerful metacharacter that can create problems if not used properly, as it matches almost any character.

---

*Source: Data Science Anywhere*

- YouTube: https://www.youtube.com/@datascienceanywhere/
- Udemy: https://www.udemy.com/user/freeai-space/
- GitHub: https://github.com/marslearnings
