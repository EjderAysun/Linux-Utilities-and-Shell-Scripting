# Lecture 01: File System and Commands

## `pwd` ⇒ print working directory (COMMAND)

## `ls` ⇒ list (COMMAND)

-   Giving `ls` command lists the contents of the current directory.
-   **`-rw-r--r--`** ⇒ shows the access permissions (it is not a command)

|Option|Long Option|Description|
|---|---|---|
|**`-l`**||list in long format (get information about a file)|
|**`-h`**|`-human-readable`|make file size is human readable, <ins>Ex:</ins> (4096 to 4.0K)|
|**`-a`**|`--all`|list all files, including hidden files|
|**`-d`**|`--directory`|show info about the directory, do not list the directory contents|
|**`-r`**|`--reverse`|display in reverse order (the default in ls is alphabetical)|
|**`-S`**||sort results by file size|
|**`-t`**||sort by modification time|

## Viewing Files

-   In Linux *“every thing is a file”*
-   **`file`** (COMMAND)
    -   `file` command can be used to determine a file’s type.
    -   `file [option] [filename]`
-   **`cat` ⇒ concatenation** (COMMAND)
    -   `cat` command actually concatenates and prints files. It is mostly used to combine two or more files.
    -   If only one file is given, that file is written to the screen.
    -   **Shift + Page Up** and **Shift + Page Down** can be used to scroll the output, but it has a limit. If the file is longer than the limit, there will be some missing information.
-   **`more`** (COMMAND)
    -   If file is longer than the screen size, `more` command displays until the screen is filled, and waits for the user to press **ENTER** to continue line by line.
    -   Can be quit with the **q** key.
-   **`less`** (COMMAND)
    -   `less` can show the contents of a file one screen at a time, allows you to go back and forth, search the file etc.
    -   **Up** and **down arrow keys** or the **page up** and **down keys** can be used.
    -   Can be quit with the **q** key.
    -   When a file is loaded, forward slash key, /, can be used to enter a string to search. This starts a text input line on the bottom left corner.
-   **`man [other command]`** ⇒ manual command uses this interface to display a command’s **manual page**. These features can be used there, as well.
-   **`wc` ⇒ word count** (COMMAND)
    -   `wc` that counts words, lines, characters or bytes.
    -   By default it shows lines, words and bytes contained in the input file.
    -   The `-l` option displays only the number of lines.

## Wildcards
- They are a feature of the shell that help us select a group of files by using special characters.
- Basic Wildcards:
|Wildcard|Meaning|
|---|---|
|**`*`**|Matches any character|
|**`?`**|Matches a single character|
|**`[chars]`**|Matches any character in a set of characters|
|**`[!chars]`**|Matches any character NOT in a set of characters|
- **Wildcard `*`**
    - The star, *, matches any number of characters.  
    <ins>Ex</ins>: To list all the files that end with _png_: `ls *png`  
    <ins>Ex</ins>: It can be used between strings, like files that start with _lab_ and end with _pdf_ can be listed as: `ls lab*pdf`
- **Wildcard `?`**
    - The question mark, ?, matches a single character.
    - It can be used to say that expected any character in that position of the string.  
    <ins>Ex:</ins> `ls lab?.pdf` selects files such as lab0.pdf, lab1.pdf, laba.pdf, labk.pdf, labq.pdf, ...  
    <ins>Ex:</ins> It can be used as many as required: `ls lab_???.pdf` selects files such as lab_123.pdf, lab_a12.pdf, lab_65t.pdf, lab_dfg.pdf, ...
- **Wildcard `[]`**
    - The square brackets [], matches one character from a set of characters.  
    <ins>Ex:</ins> `ls lab[0k4].pdf` selects files such as lab0.pdf, labk.pdf or lab4.pdf but not lab3.pdf, lab5.pdf, laba.pdf.
    - Here is a very common way to use it: `ls [Pp]roblem[Ss]olving.pdf`
    - Exclamation mark, !, can be used to negate the selection.  
    <ins>Ex:</ins> `ls lab[0k4].pdf` this time file names lab0.pdf, labk.pdf or lab4.pdf will not be selected, but files such as lab3.pdf, lab5.pdf, laba.pdf, etc.
    ### More Wildcards
There are other wildcards that might improve your selection possibilities.
- **Wildcard `{}`**
    -   Similar to matching a single character from a set of characters, we can also match set of characters.
    -   The curly braces define a list of strings that you can use to match.  
    Ex: `ls lab{data_structures,10,11,12,13,14,15,linux}.pdf` matches file starts with lab, continued with one of the strings in the curly braces, and end with .pdf.  
(_Care must be taken that there is no space after the comma, otherwise it will be an erroneous use!_)
- **Range of Characters**  
    - What if we want to select file names that start with an alphabetic character, followed by a number and ends with pdf?: `ls [abcdefghijklmnopqrstuvwxyz][0123456789]pdf`. In the range structure this can be expressed as follows: `ls [a-z][0-9]pdf`.
    - What if we want to use both uppercase and lowercase letters?: `ls [a-zA-Z][0-9]pdf`
- **Class Definitions**
    - If the full range is required, then you can use the class definitions. If another range is required, such as i to m, or 4 to 13, then the range syntax can be used.
    - Here's the same command as the previous example using class definitions: `ls [[:lower:]][[:digit:]].pdf`
|Character Class|Meaning|
|---|---|
|`[:alnum:]`|Matches any alphanumeric characters (both alphabetic and numerals)|
|`[:alpha:]`|Matches any alphabetic characters|
|`[:digit:]`|Matches any numeral|
|`[:lower:]`|Matches any lower-case letter|
|`[:upper:]`|Matches any upper-case letter|