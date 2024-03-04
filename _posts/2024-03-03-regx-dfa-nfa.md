---
layout: post
title: "Reg X and DFA"
date: 2024-03-03
categories: general
---

**Front Notes**

* I found the MIT open lectures by Michael Sipser and the Easy Theory YouTube channel to be incredibly helpful in understanding the course material. Most importantly, avoid Eberly at all cost.

**What are Regular Expressions?**

* A regular expression (regex) is a sequence of characters that defines a search pattern within text. Regexes are incredibly powerful for finding, matching, replacing, and extracting specific pieces of information from larger strings.

**Why Learn Regex?**

* **Text Manipulation:** Regex makes complex text processing tasks a breeze.
* **Efficiency:**  A single regex pattern can replace lines of traditional code.
* **Data Validation:** Ensure user input (like emails or phone numbers) follow the correct format.
* **Web Scraping:** Extract targeted data from websites.
* **Code Cleanup:** Refactor code and find patterns.

**Basic Building Blocks**

* **Literals:** The simplest regex elements are plain characters.
   *  Example: "cat" matches the literal word "cat".
* **Metacharacters:** These have special meanings in regex.
    * **.** (Period): Matches any single character (except newline, usually).
       Example: "c.t" matches "cat", "cot", "c#t", etc.
    * **\d**: Matches a single digit (0-9).
    * **\w**: Matches a single word character (letter, number, or underscore).
    * **[]**: Character class. Matches any character inside the brackets.
       Example: "[abc]" matches "a", "b", or "c". 
    * **^**: Matches the beginning of a string or line.
       Example: "^Hello" matches "Hello World" but not "Some text Hello"
    * **$**: Matches the end of a string or line
       Example: "World$" matches "Hello World" but not "Hello World Again"
* **Quantifiers:** Specify how many times an element should repeat.
   * **\***: Zero or more times.
      Example: "colou*r" matches "color" and "colour".
   * **\+**: One or more times.
      Example: "\d+" matches "123" but not "".
   * **?**: Zero or one time.
      Example: "Nov(ember)?" matches "Nov" and "November".
   * **{n}**: Exactly 'n' times.
      Example: "\d{3}" matches three-digit numbers.
   * **{n,m}**: At least 'n' times, at most 'm' times.

**Example: Email Validation**

A basic email regex:

```
/^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/
```

**String Operations vs. Language Operations**

* **String Operations:**
    * **Find Matches:** Regex can check if a pattern exists within a string.
    * **Extract Matches:** Isolate and capture specific parts of a string.
    * **Replace Matches:** Substitute text with new content based on the regex pattern.
    * **Split String:** Divide a string into substrings using a regex as the delimiter.
* **Language Operations:**   
    * **Groups ( )**: Used for capturing parts of a match.
       Example:  "(\d{3})-(\d{3})-(\d{4})" captures three number groups in a phone number.
    * **Alternation ( | ):**  A sort of "or" operator.
       Example: "cat|dog" matches either "cat" or "dog".

**Note on Notation**

You'll sometimes see the union symbol (U) used in set theory in the context of regular expressions.  The '+' symbol often serves the same purpose.

**Tools and Practice**

* **Websites:**
    * regex101: [https://regex101.com/](https://regex101.com/) (Test, build, and debug regex with explanations)
    * RegExr: [https://regexr.com/](https://regexr.com/) (Learn and experiment interactively)
* **Most programming languages** (Python, JavaScript, Java, etc.) support regex.


---
<br>
<br>
<br>

**What are Finite Automata?**

* A Finite Automaton (FA) is a simple mathematical model of a machine that reads input symbols and transitions between states based on those symbols.
* FAs are used to recognize patterns within input strings.
* There are two main types:
   * **Deterministic Finite Automata (DFA)**: For each state and input symbol, there is exactly one possible next state.
   * **Nondeterministic Finite Automata (NFA)**: For each state and input symbol, there can be multiple next states, or even no transitions at all.  

**Components of a DFA**

1. **States (Q):** Represented by circles.
2. **Input Alphabet (Σ):**  The set of valid symbols.
3. **Transition Function (δ):**  Defines how the DFA moves from one state to another based on input symbols (represented by arrows).
4. **Start State (q0):**  The initial state (usually has an arrow pointing to it from nowhere).
5. **Accept State(s) (F):** If the machine ends in an accept state after reading the input string, the string is accepted (usually marked with a double circle).

**Example: DFA Recognizing Strings Ending in "01"**

* **States:** {q0, q1, q2}
* **Alphabet:** {0, 1}
* **Start State:** q0
* **Accept State:** q2 
* **Transition Function:** See the diagram below

![Alt text for the image](/assets/images/regx.png)

**Regular Expressions and Languages**

* **Regular Expression:** A pattern defining a set of strings.
* **Language:** The set of strings accepted by a DFA or described by a regular expression.

**For the Above DFA:**

* **Regular Expression:** (0+1)*01 
* **Language:**  All strings over the alphabet {0, 1} that end in "01".

**How DFAs Work**

1. Start in the initial state.
2. Read input symbols one by one.
3. Follow transitions based on the current state and input symbol.
4. If the input is completely read and the DFA is in an accept state, the string is accepted. Otherwise, it's rejected.

**Key Points**

* DFAs and Regular Expressions are closely related.  Every regular expression has an equivalent DFA, and vice versa
* NFAs are more flexible, but both can recognize the same class of languages (regular languages).


