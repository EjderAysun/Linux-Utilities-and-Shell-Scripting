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
    > <ins>Ex:</ins> To list all the files that end with _png_: `ls *png`  
    - It can be used between strings.  
    > <ins>Ex:</ins> Files that start with _lab_ and end with _pdf_ can be listed as: `ls lab*pdf`
- **Wildcard `?`**
    - The question mark, ?, matches a single character.
    - It can be used to say that expected any character in that position of the string.  
    > <ins>Ex:</ins> `ls lab?.pdf` selects files such as lab0.pdf, lab1.pdf, laba.pdf, labk.pdf, labq.pdf, ...
    - It can be used as many as required.  
    > <ins>Ex:</ins>`ls lab_???.pdf` selects files such as lab_123.pdf, lab_a12.pdf, lab_65t.pdf, lab_dfg.pdf, ...
- **Wildcard `[]`**
    - The square brackets [], matches one character from a set of characters.  
    > <ins>Ex:</ins> `ls lab[0k4].pdf` selects files such as lab0.pdf, labk.pdf or lab4.pdf but not lab3.pdf, lab5.pdf, laba.pdf.
    > - Here is a very common way to use it: `ls [Pp]roblem[Ss]olving.pdf`
    - Exclamation mark, **!**, can be used to negate the selection.  
    > <ins>Ex:</ins> `ls lab[!0k4].pdf` this time file names lab0.pdf, labk.pdf or lab4.pdf will not be selected, but files such as lab3.pdf, lab5.pdf, laba.pdf, etc.
    ### More Wildcards
There are other wildcards that might improve your selection possibilities.
- **Wildcard `{}`**
    -   Similar to matching a single character from a set of characters, we can also match set of characters.
    -   The curly braces define a list of strings that you can use to match.  
    > <ins>Ex:</ins> `ls lab{data_structures,10,11,12,13,14,15,linux}.pdf` matches file starts with lab, continued with one of the strings in the curly braces, and end with .pdf.  
(_Care must be taken that there is no space after the comma, otherwise it will be an erroneous use!_)
- **Range of Characters**  
    - **What if we want to select file names that start with an alphabetic character, followed by a number and ends with pdf?**  
    > <ins>Answer:</ins> `ls [abcdefghijklmnopqrstuvwxyz][0123456789]pdf`. In the range structure this can be expressed as follows: `ls [a-z][0-9]pdf`.
    - **What if we want to use both uppercase and lowercase letters?**
    > <ins>Answer:</ins> `ls [a-zA-Z][0-9]pdf`
- **Class Definitions**
    - If the full range is required, then you can use the class definitions. If another range is required, such as i to m, or 4 to 13, then the range syntax can be used.
    - Here's the same command as the previous example using class definitions:  
    `ls [[:lower:]][[:digit:]].pdf`  

        |Character Class|Meaning|
        |---|---|
        |`[:alnum:]`|Matches any alphanumeric characters (both alphabetic and numerals)|
        |`[:alpha:]`|Matches any alphabetic characters|
        |`[:digit:]`|Matches any numeral|
        |`[:lower:]`|Matches any lower-case letter|
        |`[:upper:]`|Matches any upper-case letter|

## Basic Commands
- **`mkdir` ⇒ make directory** (COMMAND)
    - Create a new directory by giving the path of the new directory.  
    > <ins>Ex:</ins>  
    `mkdir Linux`  
    `mkdir /home/ejder/Desktop/Labs`
    - More than one path can be given. In this case, mkdir will create all of them.  
    > <ins>Ex:</ins> `mkdir dir1 dir2 dir3 dir4`
- **`cp` ⇒ copy** (COMMAND)
    - It copies files and directories.
    - It can be copy one or more files to a new path.  
    > <ins>Ex:</ins> `cp file1 file2` This command copies file1 to file2. Both of these are actually relative paths. There will be a copy of file1 in the same directory, and its name will be file2.  
    > <ins>Ex:</ins> `cp /home/ejder/file1 /usr/bin` This command copies file1 to the /usr/bin directory. Since a new name is not supplied, the file will be copied using its original name. The absolute path of the new file will be /usr/bin/file1.
    - It is also possible to copy a list of files to a new directory. Since there will be more than one file, the destination path must be a directory.  
    > <ins>Ex:</ins> `cp file1 file2 file3 /etc/files`
    - When files are copied, the copies take on the default attributes of the user performing the copy. Their permissions will be updated.  

        |Option|Long Option|Description|
        |---|---|---|
        |**`-a`**|**`--archive`**|Option copies the files and directories and all of their attributes, including ownerships and permissions.|
        |**`-i`**|**`--interactive`**|Option enables interactive mode. In this case, cp will ask for confirmation to overwrite an existing file. If you do not supply this option, cp will silently overwrite the files.|
        |**`-v`**|**`--verbose`**|Option enables the verbose mode, where cp prints informative messages as the copy is performed.|
        |**`-u`**|**`--update`**|Option is the update mode, cp only copies if the files do not exist in the destination path, or are newer than the existing corresponding files.|

    - The `-r`(`--recursive`) option is the recursive mode, copies files and directories.  
    > <ins>Ex:</ins> `cp -r /home/ejder/Desktop /home/ejder/backup` To copy the /home/ejder/Desktop directory to /home/ejder/backup, this command can be used.
    - The single dot (`.`) was the pointer for the current directory, double dots (`..`) was the pointer for the parent directory. These can be used for relative paths in the cp command.  
    > <ins>Ex:</ins> `cp /etc/* .` This command copies all files from /etc to current directory.
- **`mv` ⇒ move** (COMMAND)
    - `mv` command moves files and directories from one path (=the source), to another path (=the destination).
    - It is like `cp` command, it even shares its following options: `-i`, `-u`, `-v`  
    > <ins>Ex:</ins> `mv file1 /home/ejder/Desktop` This command moves the file1 to a new location(Desktop).
    - If the source and target directories are the same, then the file is **renamed**.
    > <ins>Ex:</ins> `mv file1 file2` This command renames file1 to file2.
    - A list of files can be moved into a directory as well.  
    > <ins>Ex:</ins> `mv file1 file2 file3 dir1/` This command moves the files to directory dir1. This directory must exist for this command to work.
- **`rm` ⇒ remove** (COMMAND)
    - `rm` command removes files and directories.
    - To remove directories, the recursive option `-r` (`--recursive`) must be used.
    > <ins>Ex:</ins> `rm file1 file2` this command removes file1 and file2 files.   
    > <ins>Ex:</ins> `rm -r dir1` this command removes dir1 directory.
    - The interactive (`-i`) and verbose (`-v`) options are also available.
    - There is also a `-f` (`--force`) option, where the non-existent files are silently ignored and the interactive option is overwritten; which means `rm` never prompts for confirmation.
    - There is no "Recycle Bin" in Linux. If a file is removed, it is gone forever.
    - Be very careful with the `-rm` command, especially when using wildcards.
    - Consider the situation when you want to delete all the HTML files, but instead of using wildcardsas `*.html`, a space is used between the star and the dot: `rm * .html`. To make sure that you are deleting the correct files when using a wildcard, check the `ls` command first. If the correct files are listed, then you can use the `rm` command.

## Hard and Soft Links
### Hard Links
- Files are made up two parts:
    - the data part, containing the file's content
    - the name part, which holds the file's name
- Since every file has a name, each file has a hard link by default.
- In the long listing format with the ls command, the second column shows the number of hard links of the file.   
> <ins>Ex:</ins> _Output:_ `-rw-r--r-- 3 ejder ejder   397985 Mar 28 15:10  world.sql`  
The second column (3) is the number of hard links.
- When created another hard link for the file, we create additional name parts that all refer to the same data part. The system assigns a chain of disk blocks to an **inode**, which is then associated with the name part.
- Each hard link therefore refers to a specific inode containing the file's contents.
- To do so, `ln` command can be used:
> <ins>Ex:</ins> `ln world.sql kepler452b.sql`  
        ![ln_command](https://github.com/user-attachments/assets/5f35f32d-c197-46ec-a776-29c81658f839)
- Now that we have created a new hard link, the long listing shows both of these files. The hard link column is correctly listed as 2 for world.sql and kepler452b.sql. However, **how can it be know that they are the same file? There can be two files that have the same time stamp, the same size, etc. The same data can be contained even in two different files. How can it be check that they both point to the same file?**  
> <ins>Answer:</ins>  
        ![-li_or_-i_option](https://github.com/user-attachments/assets/d7169c6b-1007-485e-8735-21427941873e)
- The `-i` (`--inode`) option of the `ls` command prints the index number of each file. **What happens if you delete one of these files? When is the file really deleted?**
- <ins>Answer:</ins> The data part of the file is deleted when the last hard link to the file is deleted. So, to completely remove a file, all of its hard links must be deleted. There are two important limitations to hard links:
    - A hard link can not reference a file outside its own file system. This means a link may not reference a file that is not on the same partition as the link itself.
    - A hard link may not reference a directory.
### Soft Links
- Soft links (symbolic links) were created to overcome the limitations of the hard links.
- They work with a special type of file that contains a text pointer to the referenced file or directory.
- The `ln` command, with the `-s` (`--symbolic`) option is used to create symbolic links.  
    > <ins>Ex:</ins> `ln -s world.sql earth.sql`
- The symbolic name is actually a path.
- The symbolic link will look for the file using this path. Therefore, if the target file is moved (or deleted), the link will be broken.
- The size of the symbolic links is very small, since it is only a link, not the original file.
    > <ins>Ex:</ins>  
        ![ln_-s_option](https://github.com/user-attachments/assets/0d9d9412-2330-4310-8f34-8b5fc69fa176)
- **Why do we need symbolic links?** 
    > <ins>Answer:</ins> Suppose we have a library: A.1.4.1. When a program is compiled, it is usually linked to this shared object (or dynamic library). However, updates are common, and the next minor version might be A.1.5.0. When this minor update arrives, the executables won't be able to locate the shared object and will terminate with an error message. Most of the libraries are given a symbolic link, with a major version number. Symbolic link A.1 can be points to A.1.4.1. When a new minor update arrives, A.1 will point to the update. So the executables will run without noticing any change.
## Command Types
- **An Executable Program:** The command is an executable file, compiled or interpreted (a script), that resides in a directory. The usual locations are /bin, /usr/bin, etc. You can use the **`which`** command to locate the path of a command.
- **A command built into shell itself:** Similar to **`cd`**, there are some shell built-in commands.
- **A shell function:** Functions are small bash scripts that are incorporated into the shell.
- **An alias:** We can derive new commands from existing ones.
- **How can be know which is which?** The easiest way is to use the **`type`** command.  
> <ins>Ex:</ins>  
    ![type_and_which_command](https://github.com/user-attachments/assets/80aa65f0-a4dd-4db2-acdc-b2a05d49df6f)

## Manuals
- Manuals are the best references when you are stuck. There are manuals for the executable files. However, there are also manuals for administrative commands, programming interfaces, file formats, etc. These are called sections and can be referred to them. The following slides contains the list of sections:  
    |Section|Contents|
    |---|---|
    |1|User commands|
    |2|Prog. Interfaces, kernel system calls|
    |3|Prog. Interfaces to C library|
    |4|Special files such as nodes|
    |5|File formats|
    |6|Games and amusements|
    |7|Miscellaneous|
    |8|System Administration Commands|

> <ins>Ex:</ins> There is a hostname configuration file, hostname resolution description and a **`hostname`** command as well. If we type `man hostname`, we get the `hostname` command manual page. Since `hostname` supports many sections, it displays the first matched entry. It can be searched using **`whatis`** command, which gives a short description of the command.  
    ![whatis_command](https://github.com/user-attachments/assets/092f0ccf-8eea-467c-9e52-872e637919e2)  
> It also displays the manual page section number. To read the third section, the one about the C, `man 5 hostname` can be used.  
    ![man_command](https://github.com/user-attachments/assets/2f9d808c-65b1-46a7-aece-b478bb143222)