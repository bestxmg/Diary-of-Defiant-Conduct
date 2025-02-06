WIP
### **Full Usage of Regular Expressions (Regex)**

A **regular expression (regex)** is a powerful tool used for matching patterns in text. It's widely used for tasks like searching, replacing, validating, and extracting text data in programming, text processing, and data analysis.

Here’s a detailed guide to the usage of regular expressions, including syntax, common operations, and practical examples:

---

### **1. Basic Syntax**

- **Literal characters**: Match exactly as they are.
  - Example: `a` matches the character "a".
  
- **Metacharacters**: Special characters that have specific meanings:
  - **`.`**: Matches any character except newline.
    - Example: `a.b` matches `a`, followed by any character, followed by `b` (e.g., "acb").
  - **`^`**: Matches the start of the string.
    - Example: `^abc` matches "abc" only if it appears at the start of the string.
  - **`$`**: Matches the end of the string.
    - Example: `abc$` matches "abc" only if it appears at the end of the string.
  - **`[]`**: Matches any one of the characters inside the brackets.
    - Example: `[aeiou]` matches any single vowel.
  - **`|`**: Acts as a logical OR.
    - Example: `abc|def` matches "abc" or "def".
  - **`()`**: Groups patterns together.
    - Example: `(abc|def)` matches "abc" or "def" as a group.

### **2. Character Classes**

Character classes define a set of characters that can be matched:

- **`[abc]`**: Matches any of the characters `a`, `b`, or `c`.
- **`[^abc]`**: Matches any character except `a`, `b`, or `c`.
- **`\d`**: Matches any digit (`0-9`).
- **`\D`**: Matches any non-digit character.
- **`\w`**: Matches any word character (letters, digits, or underscore).
- **`\W`**: Matches any non-word character.
- **`\s`**: Matches any whitespace character (space, tab, newline).
- **`\S`**: Matches any non-whitespace character.
- **`\b`**: Matches a word boundary (e.g., space or punctuation).
- **`\B`**: Matches a non-word boundary.

### **3. Quantifiers**

Quantifiers specify the number of times an element should appear:

- **`*`**: Matches 0 or more occurrences of the preceding character or group.
  - Example: `a*b` matches `b`, `ab`, `aab`, `aaab`, etc.
- **`+`**: Matches 1 or more occurrences of the preceding character or group.
  - Example: `a+b` matches `ab`, `aab`, `aaab`, etc., but not `b`.
- **`?`**: Matches 0 or 1 occurrence of the preceding character or group.
  - Example: `a?b` matches `b` or `ab`.
- **`{n}`**: Matches exactly `n` occurrences of the preceding character or group.
  - Example: `a{3}` matches exactly `aaa`.
- **`{n,}`**: Matches `n` or more occurrences of the preceding character or group.
  - Example: `a{2,}` matches `aa`, `aaa`, `aaaa`, etc.
- **`{n,m}`**: Matches between `n` and `m` occurrences of the preceding character or group.
  - Example: `a{2,4}` matches `aa`, `aaa`, or `aaaa`.

### **4. Anchors**

- **`^`**: Asserts that the match occurs at the start of the string.
  - Example: `^abc` will match only if the string starts with "abc".
- **`$`**: Asserts that the match occurs at the end of the string.
  - Example: `abc$` will match only if the string ends with "abc".

### **5. Escaping Special Characters**

Some characters have special meanings in regex. To match them literally, you need to escape them with a backslash (`\`).

- Example: To match a dot (`.`), use `\.`.
- Example: To match a backslash (`\`), use `\\`.

### **6. Groups and Capturing**

- **()`**: Grouping is used to group parts of the regex.
  - Example: `(abc|def)` matches "abc" or "def".
  
- **Capturing Groups**: Parts of the match can be captured into groups, which can be referenced later.
  - Example: `(\d{3})-(\d{3})-(\d{4})` captures phone numbers as groups.
  - In programming, you can extract these groups and use them in your code.

### **7. Lookahead and Lookbehind (Assertions)**

Lookahead and lookbehind are used to match a pattern only if it is followed or preceded by another pattern.

- **Lookahead (`?=`)**: Matches a group only if it is followed by a specific pattern.
  - Example: `\d(?=\D)` matches a digit only if it is followed by a non-digit.
  
- **Negative Lookahead (`?!`)**: Matches a group only if it is **not** followed by a specific pattern.
  - Example: `\d(?!\D)` matches a digit only if it is not followed by a non-digit.
  
- **Lookbehind (`?<=`)**: Matches a group only if it is preceded by a specific pattern.
  - Example: `(?<=\d)\D` matches a non-digit only if it is preceded by a digit.
  
- **Negative Lookbehind (`?<!`)**: Matches a group only if it is **not** preceded by a specific pattern.
  - Example: `(?<!\d)\D` matches a non-digit only if it is not preceded by a digit.

### **8. Regex Flags (Modifiers)**

Flags modify the behavior of regular expressions:

- **`i`**: Makes the regex case-insensitive.
  - Example: `/abc/i` matches `abc`, `ABC`, `aBc`, etc.
- **`g`**: Global match; finds all matches in a string (not just the first).
  - Example: `/a/g` finds all `a` characters in a string.
- **`m`**: Multiline; makes `^` and `$` match the start and end of each line.
  - Example: `/^abc/m` matches `abc` at the start of each line.
- **`s`**: Dot matches newlines; allows the dot (`.`) to match newlines as well.
  - Example: `/a.b/s` matches `a`, any character, and `b`, even if there is a newline between them.

---

### **Common Use Cases for Regular Expressions**

#### **1. Validation**
- **Email Validation**: Ensure that the email follows the correct format.
  ```regex
  ^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$
  ```
- **Phone Number Validation**: Match phone numbers with specific formats.
  ```regex
  ^\(\d{3}\) \d{3}-\d{4}$
  ```

#### **2. Search and Replace**
- **Find and Replace a Word**: Replace all occurrences of "apple" with "orange".
  ```regex
  s/apple/orange/g
  ```
  
#### **3. Extracting Data**
- **Extract Dates**: Find all dates in the format `MM/DD/YYYY`.
  ```regex
  \b\d{2}/\d{2}/\d{4}\b
  ```

#### **4. Log Parsing**
- **Extract IP Addresses**: Find all IP addresses in logs.
  ```regex
  \b\d{1,3}(\.\d{1,3}){3}\b
  ```

#### **5. Text Processing**
- **Split Text**: Split a text by spaces or punctuation marks.
  ```regex
  [\s,;.!?]+
  ```

---

### **Conclusion**

Regular expressions are a versatile tool used for pattern matching, text validation, text extraction, and manipulation across a wide variety of platforms. They are widely used in programming languages like **Python**, **JavaScript**, **Java**, **C++**, and command-line tools like **grep** and **sed**.

By mastering regex syntax, you'll be able to efficiently handle tasks related to text processing in a concise and powerful way.