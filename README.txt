THIS PROJECT IS DONE BY 2024CS10410
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
FILES:-
1.heap.hpp
2.Tree.hpp
3.build.ps1
4.map.hpp
5.test.cpp //main file
6.README.txt
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
HOW TO RUN:-
1. OPEN THE TERMINAL/POWERSHELL IN YOUR OS.
2. CHANGE THE DIRECTORY WITH THE COMMAND "cd <directory location of the folder with files extracted>", example- "cd C:\Users\Hp\Documents\assignment"
3. BYPASS THE EXECUTION POLICY BY THIS COMMAND "Set-ExecutionPolicy -Scope Process Bypass"
4. TYPE ".\build.ps1" TO OPEN THE SHELL SCRIPT

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

SYNTAX FOR VALID COMMANDS:-
1.CREATE <filename> Creates a file with a root version (ID 0), empty content, and an initial snapshot
  message("THIS IS ROOT").

2.READ <filename> Displays the content of the file’s currently active version.

3.INSERT <filename> <content> Appends content to the file. This creates a new version if the active
version is already a snapshot; otherwise, it modifies the active version in place.

4.UPDATE <filename> <content> Replaces the file’s content. This creates a new version with given content if current version is already a snapshot.

5.SNAPSHOT <filename> <message> Marks the active version as a snapshot, making its content immutable. It stores the provided message and the current time.

6. ROLLBACK <filename> [versionID] Sets the active version pointer to the specified versionID. If no ID is provided, it rolls back to the parent of the current active version.

7.HISTORY <filename> Lists all snapshotted versions of the file chronologically, which lie on the path 
  from active node to the root in the file tree, showing their ID, timestamp, and message.

8. RECENT_FILES <num> Lists files in descending order of their last modification time restricted to the first num entries.

9. BIG_TREES <num> Lists files in descending order of their total version count restricted to the first num entries.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

ERROR HANDLING 	:-
1. Anything except these commands would result in invalid input.
2. If num given to RECENT_FILES or BIG_TREES exceeds the number of current files then it will displays information of all the files.
3. If empty filename is given with any function call , or an invalid number the program will throw invalid input verdict ,and wait for next input.
4. extra information is ignored in case a function requires only one string to work on for example (" CREATE TEXT.txt hello", "HISTORY TEXT.txt hello", "RECENT_FILES 12 hello" ) in all the cases "hello" will be ignored and remaining command will be executed if valid.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

IMPORTANT INFO:-
1. filename cant be empty , and it should not contain spaces, otherwise program will take whatever given before trailing space as filename.
2. content and messages can contain spaces and can be empty as well.
3. RECENT_FILES works under seconds precision, means it will give arbitrary ordering of files if they are modified within same second.
4. The content of root is kept empty and it is always a snapshot.
5. using insert ,update on a file changes its modification time .
6. filenames can't be duplicated, and if you try you will be given the verdict "FILE ALREADY EXISTS".
7. Type "exit" in lowercase to exit the program.
8. enter lines of code sequentially 
9. comparators are used for heap sort(nodect, modifiedtime), which sorts on basis of number of nodes and modification time respectively.
10. rollback from root will do nothing and current version would still be at root, no error thrown during this.
11. use UPDATE ,INSERT with caution , commands like "UPDATE <FILE>" without any content will be considered as passing empty string and would result in content being empty,since i am allowing content to be empty(2*).

