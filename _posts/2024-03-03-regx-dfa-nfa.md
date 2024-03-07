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
---
<br>
<br>
<br>

### Claim

For a deterministic finite automaton (DFA) designed to recognize the language L(M) consisting of strings with an even number of 0's, we define two states: \(q_0\) and \(q_1\). State \(q_0\) is reached after processing an even number of 0's, and state \(q_1\) is reached after processing an odd number of 0's.

### Proof by Induction

We will use proof by induction on the length of the input to demonstrate that our DFA correctly ends in state \(q_0\) for inputs with an even number of 0's and in state \(q_1\) for inputs with an odd number of 0's.

#### Base Case: \(k=0\)

For the input \(\lambda\) (the empty string), the length of the input is 0. Since the empty string contains an even number of 0's (zero is even), the transition ends in state \(q_0\). This establishes our base case.

#### Inductive Step

Let's assume our claim holds for all strings of length \(k\). Now, consider an input of length \(k+1\), represented as \(x = x_1x_2x_3...x_{k+1}\).

##### Case 1: \(x\) has an odd number of 0's.

To demonstrate that the DFA ends in state \(q_1\), we decompose \(x\) into \(a0b\), where \(a\) contains an even number of 0's and \(b\) contains no 0's. After processing \(a\), the DFA is in state \(q_0\) by our inductive hypothesis, since \(a\) has an even number of 0's.

When the DFA processes the 0 in \(a0b\), it transitions from \(q_0\) to \(q_1\), reflecting the odd number of 0's processed up to this point. Since \(b\) contains no 0's, processing \(b\) does not change the state, and the DFA remains in \(q_1\).

##### Case 2: \(x\) has an even number of 0's.

Let's split this case into two scenarios for clarity:

1. **\(x\) ends with a non-zero element**: In this case, removing the last element does not change the parity of 0's in \(x\). By the inductive hypothesis, if \(x\) without the last element ends in \(q_0\), then \(x\) itself also ends in \(q_0\), as the last element does not affect the state transition for 0's.

2. **\(x\) is formed by adding a 0 to a string with an odd number of 0's**: In this scenario, let \(x = a0\), where \(a\) has an odd number of 0's. By the inductive hypothesis, processing \(a\) would lead to state \(q_1\). Adding another 0 transitions the DFA back to \(q_0\), consistent with \(x\) having an even number of 0's.

Thus, through induction, we've shown that the DFA correctly ends in state \(q_0\) after processing strings with an even number of 0's and in state \(q_1\) after processing strings with an odd number of 0's, proving our claim.


---
<br>
<br>
<br>

####  3.5 Exercise Solution

To describe each of the languages you've listed based on the sets \(A = \{1, 00\}\) and \(B = \{11, 10, \lambda\}\), we will break down each operation and its resulting language.

### 1. \(AB\)

The language \(AB\) is formed by concatenating each string in \(A\) with each string in \(B\). This results in all possible combinations where an element from \(A\) precedes an element from \(B\).

- For \(1 \in A\):
  - Concatenating with \(11 \in B\): \(111\)
  - Concatenating with \(10 \in B\): \(110\)
  - Concatenating with \(\lambda \in B\): \(1\)

- For \(00 \in A\):
  - Concatenating with \(11 \in B\): \(0011\)
  - Concatenating with \(10 \in B\): \(0010\)
  - Concatenating with \(\lambda \in B\): \(00\)

So, \(AB = \{111, 110, 1, 0011, 0010, 00\}\).

### 2. \(BA\)

The language \(BA\) is formed by concatenating each string in \(B\) with each string in \(A\), effectively the opposite of \(AB\).

- For \(11 \in B\):
  - Concatenating with \(1 \in A\): \(111\)
  - Concatenating with \(00 \in A\): \(1100\)

- For \(10 \in B\):
  - Concatenating with \(1 \in A\): \(101\)
  - Concatenating with \(00 \in A\): \(1000\)

- For \(\lambda \in B\):
  - Concatenating with \(1 \in A\): \(1\)
  - Concatenating with \(00 \in A\): \(00\)

Thus, \(BA = \{111, 1100, 101, 1000, 1, 00\}\).

### 3. \(B^2\)

The language \(B^2\) is formed by concatenating each string in \(B\) with itself.

- \(11\) concatenated with \(11\): \(1111\)
- \(11\) concatenated with \(10\): \(1110\)
- \(11\) concatenated with \(\lambda\): \(11\)

- \(10\) concatenated with \(11\): \(1011\)
- \(10\) concatenated with \(10\): \(1010\)
- \(10\) concatenated with \(\lambda\): \(10\)

- \(\lambda\) concatenated with anything in \(B\) gives the elements of \(B\).

So, \(B^2\) includes elements like \(1111, 1110, 11, 1011, 1010, 10\), plus all elements of \(B\) because of the concatenation with \(\lambda\).

### 4. \((AB)^*\)

The language \((AB)^*\) includes all strings that can be formed by taking the language \(AB\) and concatenating its elements any number of times, including the empty string \( \lambda \) (because any language to the power of \(*\) includes the empty string by definition of the Kleene Star operation).

This language is infinite and includes \( \lambda \), \(111\), \(110\), \(1\), \(0011\), \(0010\), \(00\), combinations of these strings with themselves and each other any number of times.

### 5. \((A \cup B)^*\)

The language \((A \cup B)^*\) is the set of all strings that can be formed by taking any combination of elements from \(A\) union \(B\) (which is all elements from both \(A\) and \(B\)), and concatenating them any number of times, including none (to include \( \lambda \)).

Since \(A \cup B = \{1, 00, 11, 10, \lambda\}\), \((A \cup B)^*\) is an infinite set that includes every possible string made up of \(0\)s and \(1\)s, including the empty string \( \lambda \), because you can concatenate any elements from \(A \cup B\) in any order, any number of times.

This explanation steps through the composition and interpretation of each language operation based on the initial sets \(A\) and \(B\). Each step builds on the understanding of how operations like concatenation, union, and the Kleene Star affect the formation of new languages from the original sets.



To decide if each statement is true for every language \(A\), let's examine them one by one.

### 1. \(A^* = (A^*)^*\)

The Kleene Star operation (\(*\)) on a language \(A\) results in a language that includes all possible strings of zero or more concatenations of strings from \(A\), including the empty string \(\lambda\). Therefore, \(A^*\) includes \(\lambda\), all strings in \(A\), all strings formed by concatenating one or more strings from \(A\), and so on.

When we apply the Kleene Star operation to \(A^*\) itself to get \((A^*)^*\), we are effectively allowing zero or more concatenations of strings from \(A^*\), which already includes all possible concatenations of strings from \(A\) plus the empty string. Since \(A^*\) includes every possible concatenation of elements from \(A\), including the empty string, applying the Kleene Star operation to it again doesn't add any new strings to the language. Thus, \((A^*)^*\) does not extend the set of strings beyond what is already included in \(A^*\).

Hence, this statement is **true**: \(A^* = (A^*)^*\).

### 2. \(A^+ = (A^+)^+\)

The \(+\) operation, or Kleene Plus, on a language \(A\) results in a language that includes all possible strings of one or more concatenations of strings from \(A\), excluding the empty string \(\lambda\). \(A^+\) thus includes all strings in \(A\), all strings formed by concatenating two or more strings from \(A\), and so on.

Applying the \(+\) operation again to \(A^+\) to get \((A^+)^+\) means looking for one or more concatenations of the strings already in \(A^+\), which itself represents one or more concatenations of strings from \(A\). Since \(A^+\) already encompasses all strings that could be formed by one or more concatenations of \(A\), further applying the \(+\) operation does not introduce any new elements that weren't already included.

Therefore, this statement is **true**: \(A^+ = (A^+)^+\).

### 3. \(A^+ = (A^+)^*\)

Comparing \(A^+\) and \((A^+)^*\), the difference lies in the presence of the empty string \(\lambda\). \(A^+\) includes strings formed by one or more concatenations of \(A\), excluding \(\lambda\), while \((A^+)^*\) includes all the strings in \(A^+\) plus the empty string \(\lambda\), because the Kleene Star (\(*\)) operation allows for zero occurrences of its operand strings, which includes allowing for the empty string.

This distinction means that while \(A^+\) and \((A^+)^*\) contain all the same strings formed by concatenating elements of \(A\), \((A^+)^*\) additionally includes the empty string \(\lambda\), which \(A^+\) does not.

Thus, the statement \(A^+ = (A^+)^*\) is **false** because \((A^+)^*\) includes \(\lambda\), whereas \(A^+\) does not.



To evaluate the statement \(\{0, 1\}^* = (\{0\}\{1\})^*\), let's understand what each part represents:

- \(\{0, 1\}^*\) represents the set of all possible strings (including the empty string \(\lambda\)) that can be formed using the symbols \(0\) and \(1\). This includes strings like \(\lambda\), \(0\), \(1\), \(00\), \(01\), \(10\), \(11\), \(000\), and so forth, ad infinitum. Essentially, it encompasses every conceivable combination of \(0\)s and \(1\)s of any length.

- \((\{0\}\{1\})^*\) represents the set of all possible strings that can be formed by concatenating the string \(0\) followed by the string \(1\) any number of times, including zero times (which includes the empty string \(\lambda\)). Examples of strings in this language include \(\lambda\) (from zero concatenations), \(01\) (from one concatenation of \(0\) followed by \(1\)), \(0101\) (from two concatenations), \(010101\) (from three concatenations), and so on.

Given these definitions, the statement \(\{0, 1\}^* = (\{0\}\{1\})^*\) suggests that the set of all strings formed by any combination of \(0\)s and \(1\)s is equal to the set of strings formed by repeated concatenations of \(0\) followed by \(1\).

This statement, however, is **false**. The reason is that while \(\{0, 1\}^*\) includes any combination of \(0\)s and \(1\)s in any order, \((\{0\}\{1\})^*\) only includes those strings where every \(0\) is directly followed by a \(1\) with no \(0\)s adjacent to each other or \(1\)s adjacent to each other unless repeated in the pattern \(01\). Therefore, \((\{0\}\{1\})^*\) is a subset of \(\{0, 1\}^*\), but not equal to it. For example, the string \(00\) or \(11\) can be included in \(\{0, 1\}^*\), but not in \((\{0\}\{1\})^*\) because they do not follow the strict pattern of alternating \(0\)s and \(1\)s starting with \(0\) and followed by \(1\).


To evaluate the statement \(\{0, 1\}^* = (\{0\}^* \{1\}^*)^*\), let's analyze both sides of the equation:

1. \(\{0, 1\}^*\) represents the set of all possible strings, including the empty string (\(\lambda\)), that can be formed using the symbols \(0\) and \(1\) in any combination and order. This includes every conceivable sequence of \(0\)s and \(1\)s of any length, such as \(\lambda\), \(0\), \(1\), \(00\), \(01\), \(10\), \(11\), \(001\), \(010\), \(100\), etc.

2. \((\{0\}^* \{1\}^*)^*\) represents the set of all possible strings that can be formed by first forming strings of any number of \(0\)s (including none, which would be the empty string) followed by any number of \(1\)s (also including none) and then repeating this pattern any number of times (including not repeating it at all, which would again include the empty string). Examples of strings in this language include \(\lambda\), \(0\), \(1\), \(00\), \(11\), \(01\), \(001\), \(011\), \(000111\), etc. Essentially, it allows for any number of \(0\)s followed by any number of \(1\)s, and this pattern itself can be repeated any number of times.

Upon comparison, the statement \(\{0, 1\}^* = (\{0\}^* \{1\}^*)^*\) is **true**. This is because:

- \(\{0, 1\}^*\) allows for any sequence of \(0\)s and \(1\)s, which implicitly includes sequences of \(0\)s followed by \(1\)s, sequences of \(1\)s followed by \(0\)s, or any mix thereof.
- \((\{0\}^* \{1\}^*)^*\) explicitly constructs these sequences by first allowing any number of \(0\)s (including none), followed by any number of \(1\)s (including none), and repeating this process any number of times. This process can generate any possible sequence of \(0\)s and \(1\)s by appropriately choosing when to switch from \(0\)s to \(1\)s in each repetition of the pattern.

In essence, \((\{0\}^* \{1\}^*)^*\) provides a structured way to generate all the sequences that \(\{0, 1\}^*\) encompasses through its unrestricted combination of \(0\)s and \(1\)s. Thus, every string that can be made from \(\{0, 1\}^*\) can also be generated by \((\{0\}^* \{1\}^*)^*\), making these two languages equivalent.


To evaluate the statement \(\{0, 1\}^* = (\{0\}^* \{1\}^* \{0\}^*)^*\), let's dissect both sides for better understanding:

1. **\(\{0, 1\}^*\)**: This represents the set of all possible strings, including the empty string (\(\lambda\)), made up of \(0\)s and \(1\)s in any order and combination. This means any sequence or combination of \(0\) and \(1\), regardless of order, is included in this set. Examples include \(\lambda\), \(0\), \(1\), \(01\), \(10\), \(001\), \(110\), \(1010\), etc.

2. **\((\{0\}^* \{1\}^* \{0\}^*)^*\)**: This expression describes the set of all strings that can be formed by concatenating sequences that consist of zero or more \(0\)s, followed by zero or more \(1\)s, followed again by zero or more \(0\)s, and this pattern itself can be repeated any number of times, including not at all (which would include the empty string \(\lambda\)). Essentially, this allows for any combination of \(0\)s and \(1\)s where \(0\)s can appear before and after \(1\)s in any sequence.

Upon inspection, the statement \(\{0, 1\}^* = (\{0\}^* \{1\}^* \{0\}^*)^*\) is **true**, and here's why:

- The left-hand side (\(\{0, 1\}^*\)) includes all possible combinations of \(0\)s and \(1\)s.
- The right-hand side (\((\{0\}^* \{1\}^* \{0\}^*)^*\)) also generates any possible combination of \(0\)s and \(1\)s by allowing for \(0\)s and \(1\)s to be placed in any sequence, with the added flexibility of interspersing \(0\)s between any number of \(1\)s and vice versa, as well as beginning and ending with any number of \(0\)s.

This formulation specifically permits any sequence of \(0\)s to be followed by any sequence of \(1\)s, with an optional sequence of \(0\)s at the end, and this entire sequence can be repeated. This structure can indeed produce any sequence of \(0\)s and \(1\)s, just as the unrestricted combination on the left-hand side does. By choosing when to repeat the pattern or transition between \(0\)s and \(1\)s within each repetition, any string in \(\{0, 1\}^*\) can be generated.

Thus, because both sides can generate the same set of strings without any restriction on the order or combination of \(0\)s and \(1\)s, the languages they describe are equivalent.



The statement "If \(A \not\subseteq B\), then \(A^* \not\subseteq B^*\)" is not necessarily true in all cases. To explore this, let's first clarify the involved concepts:

- \(A \not\subseteq B\) indicates that there is at least one element in language \(A\) that is not present in language \(B\).
- \(A^*\) represents the set of all strings that can be formed by concatenating zero or more strings from \(A\), including the empty string (\(\lambda\)).
- \(B^*\) similarly represents the set of all strings that can be formed by concatenating zero or more strings from \(B\), including \(\lambda\).

The claim suggests that if there exists at least one string in \(A\) that is not in \(B\), then the set of all strings formed from \(A\) (including repetitions and combinations of its elements) cannot be a subset of the set formed from \(B\).

### Counterexample:

However, this statement can be countered by a specific example where \(A \not\subseteq B\), yet \(A^* \subseteq B^*\).

Consider:
- \(A = \{0, 11\}\)
- \(B = \{0\}\)

Here, \(A \not\subseteq B\) because \(11\) is in \(A\) but not in \(B\). However, when considering \(A^*\) and \(B^*\):
- \(A^*\) includes \(\lambda\), \(0\), \(11\), \(00\), \(011\), \(110\), \(1111\), etc.
- \(B^*\) includes \(\lambda\), \(0\), \(00\), \(000\), etc.

In this specific example, the initial premise doesn't directly apply because \(A^*\) and \(B^*\) are concerned with combinations of their elements. However, if we adjust \(B\) to also include all possible strings that can be made from the alphabet under consideration (for instance, if \(B\) included not just \(0\), but also \(1\), making \(B = \{0, 1\}\)), then \(B^*\) would include every possible string of \(0\)s and \(1\)s, including those in \(A^*\).

A better counterexample that clearly illustrates \(A^* \subseteq B^*\) even when \(A \not\subseteq B\) is difficult to construct without bending the initial premise of what \(A\) and \(B\) include. Generally, if \(A \not\subseteq B\), one might expect that certain concatenations unique to \(A^*\) (especially involving the unique elements of \(A\) not in \(B\)) could not be replicated in \(B^*\). The critical point is that whether \(A^* \subseteq B^*\) can depend on the specific contents of \(A\) and \(B\) and how their elements can be concatenated and repeated.

Let's revise the premise for clarity:

- **Correct Understanding**: If \(A \not\subseteq B\), then it's possible for \(A^*\) to contain strings not in \(B^*\), especially due to the unique elements of \(A\). However, whether \(A^*\) is not a subset of \(B^*\) will depend on the specific elements of \(A\) and \(B\) and does not hold as a general rule without further specifics about the languages.


