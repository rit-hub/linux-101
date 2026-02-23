# linux-101

# Linux & Shell Scripting Master Dictionary

This document serves as a literal translation guide for Linux commands and shell scripting concepts. In Unix-like systems, almost every cryptic keyword is an abbreviation or a historical reference.

---

## 1. System Anatomy
* **Kernel:** The "seed" or core of the operating system. It manages the CPU, memory, and hardware devices.
* **Shell:** The "outer layer" of the OS. It is the command-line interpreter that translates human text commands into actions the Kernel can understand.
* **Terminal Emulator:** A graphical window that emulates the old, physical "terminal" machines. It provides a text interface to interact with the Shell.
* **Utilities:** The individual, single-purpose software tools (like `ls` or `grep`) that you run from the shell.

---

## 2. Standard Streams & Operators
* **`stdin` (Standard Input):** The default way a program receives information (usually from your keyboard).
* **`stdout` (Standard Output):** The default way a program outputs information (usually printing it to your screen).
* **`stderr` (Standard Error):** The default stream for outputting error messages.
* **`>` (Redirection):** Takes `stdout` and pushes it into a file, overwriting the file.
* **`>>` (Append):** Takes `stdout` and adds it to the bottom of a file without overwriting.
* **`|` (Pipe):** Takes the `stdout` of the command on the left and feeds it as `stdin` to the command on the right.

---

## 3. Directory & Navigation Commands
* **`pwd` (Print Working Directory):** Displays the full, absolute path of the folder you are currently sitting in.
* **`cd` (Change Directory):** Moves your shell session into a different folder. 
* **`ls` (List):** Lists the files and directories inside the current folder.
* **`mkdir` (Make Directory):** Creates a new folder.

---

## 4. File Management Commands
* **`touch`:** Updates the "last modified" timestamp of a file. If the file does not exist, it creates a new, empty file.
* **`cp` (Copy):** Duplicates a file or directory.
* **`mv` (Move):** Moves a file to a new location. Because moving a file to the same directory with a new name is the same as renaming it, `mv` is also the rename command.
* **`rm` (Remove):** Deletes a file. (Adding `-r` makes it recursive to delete folders; `-f` forces it without asking).
* **`cat` (Concatenate):** Reads the contents of one or more files and prints them continuously to the screen. 
* **`head`:** Prints the first 10 lines of a file.
* **`tail`:** Prints the last 10 lines of a file (often used with `-f` to "follow" logs as they update in real-time).
* **`tar` (Tape Archive):** Bundles multiple files into a single archive file. Named after the historical magnetic tape drives used for backups.

---

## 5. Search & Text Processing Commands
* **`find`:** Searches the directory tree to locate files based on name, size, or modification date.
* **`grep` (Global Regular Expression Print):** Searches line-by-line inside a file for a specific pattern of text.
* **`awk` (Aho, Weinberger, Kernighan):** A powerful text-processing language named after its three creators. Used to extract specific columns of data from text streams.
* **`sed` (Stream Editor):** Edits text on the fly (like finding and replacing words) as it flows through the terminal, without opening a text editor.
* **`cut`:** Slices out specific sections or columns from a line of text based on a delimiter (like a comma or colon).
* **`sort`:** Rearranges lines of text alphabetically or numerically.
* **`uniq` (Unique):** Filters out adjacent, duplicate lines of text.
* **`jq` (JSON Query):** A command-line tool specifically for slicing, filtering, and mapping JSON data.

---

## 6. System & Process Management Commands
* **`ps` (Process Status):** Displays a snapshot of the currently running programs.
* **`top` / `htop`:** Displays a dynamic, real-time view of running processes, CPU usage, and RAM usage.
* **`kill`:** Sends a signal to a process to terminate it, using its Process ID (PID).
* **`df` (Disk Free):** Reports the amount of available disk space on your file systems.
* **`du` (Disk Usage):** Estimates and reports the amount of space a specific file or directory is taking up.
* **`uptime`:** Tells you exactly how long the machine has been running since its last reboot.
* **`whoami`:** Prints the username associated with the current effective user ID.

---

## 7. Permissions Commands
* **`chmod` (Change Mode):** Modifies the read (`r`), write (`w`), and execute (`x`) permissions of a file.
* **`chown` (Change Owner):** Changes which user and group officially "owns" a file.
* **`sudo` (Superuser DO):** Executes the following command with the elevated security privileges of the root administrator.

---

## 8. Shell Scripting Fundamentals
* **`#!/bin/bash` (Shebang):** The `#` (hash) and `!` (bang) combination at the very top of a script. It tells the operating system exactly which interpreter to use to run the script.
* **Variables (`VAR="value"`):** A labeled container for storing data in memory. Referenced later using the dollar sign (e.g., `$VAR`).
* **Arguments (`$1`, `$2`, `$@`):** Variables that automatically capture the inputs you type after the script name when running it. `$1` is the first word, `$2` is the second, and `$@` represents all of them.
* **`if` / `then` / `fi`:** The syntax for a conditional statement. It checks if a condition is true, executes the `then` block if it is, and closes the statement with `fi` ("if" spelled backward).
* **`for` / `in` / `do` / `done`:** A loop that repeats an action for every item in a list.
* **`while` / `do` / `done`:** A loop that continues to run commands as long as a specific condition remains true.
* **`case` / `esac`:** A switch statement that checks a variable against multiple possible matches. Closed with `esac` ("case" spelled backward).
* **Exit Status (`$?`):** A hidden variable that holds a number representing whether the previous command succeeded (usually `0`) or failed (any number > `0`).

## 9. Networking & Web Commands
* **`ping` (Packet Internet Groper):** Acts like submarine sonar. It sends a tiny packet of data to a server to see if it responds and tells you how long the round-trip took.
* **`curl` (Client URL):** A tool to transfer data to or from a server. Developers use this constantly to test REST APIs right from the terminal.
* **`wget` (Web Get):** Downloads files from the web directly to your current directory. It’s great for grabbing installer files or zip archives from a server.
* **`ssh` (Secure Shell):** Creates an encrypted connection to another Linux computer over the internet, allowing you to control it as if you were sitting right in front of it.
* **`scp` (Secure Copy Protocol):** Uses the SSH protocol to securely copy files from your local machine to a remote server (or vice versa).
* **`ss` (Socket Statistics):** Investigates network sockets. It shows you what ports are open on your machine and who is connecting to them (replaces the older `netstat` command).

## 10. System Services & Background Jobs
* **`systemctl` (System Control):** The command used to control `systemd`, which is the system and service manager for modern Linux. You use this to `start`, `stop`, `restart`, or `enable` background services (like a web server or database).
* **`journalctl` (Journal Control):** Queries the logs collected by `systemd`. If a background service crashes, this is where you go to read the error logs.
* **`cron` / `crontab` (Chronos Table):** Named after the Greek word for time. A time-based job scheduler. You edit the "crontab" to tell the system to run a specific script automatically at specific minutes, hours, or days.
* **`nohup` (No Hang Up):** If you start a script and close your terminal window, the script stops. Running a command with `nohup` tells the system to ignore the "hang up" signal so the process keeps running in the background.

## 11. Advanced Scripting Keywords
* **`export`:** When you create a variable, it only exists in that specific script. `export` makes that variable an "Environment Variable," meaning any child process or script launched from there can also read it.
* **`source` (or `.`):** Reads and executes commands from a file inside the *current* shell environment instead of starting a new one. Often used to reload configuration files like `source ~/.bashrc`.
* **`read`:** Pauses the script and waits for the user to type something in, saving their input as a variable.
* **`eval` (Evaluate):** Takes a string of text and forces the shell to execute it as if it were a typed command. Powerful, but dangerous if used with untrusted input.
* **`trap`:** "Traps" system signals (like when a user presses `Ctrl+C` to kill a script). It allows you to run a cleanup function to delete temporary files before the script actually exits.
* **`shift`:** Shifts the positional arguments (`$1`, `$2`, etc.) one step to the left. `$2` becomes `$1`, `$3` becomes `$2`. Used when parsing a long list of user arguments.
