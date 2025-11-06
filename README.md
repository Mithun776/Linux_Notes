# 🧭 Linux Commands Notes

---

# 🧩 **Section 1: Introduction to Linux & Basic Commands**

---

### 🧠 **What is Linux?**

* **Linux** is an open-source, UNIX-like operating system kernel developed by Linus Torvalds in 1991.
* It powers servers, desktops, mobile systems (like Android), and even embedded devices.
* It’s known for **stability, security, and flexibility**.
* Various **distributions (distros)** exist:

  * **Ubuntu, Debian** → beginner-friendly
  * **CentOS, RHEL** → enterprise
  * **Arch, Kali** → advanced or specialized

---

### 🧭 **Understanding the Linux File System**

Linux uses a **hierarchical directory structure** starting at the root `/`.

| Directory | Description                          |
| --------- | ------------------------------------ |
| `/`       | Root directory (base of file system) |
| `/home`   | User home directories                |
| `/bin`    | Essential binaries (commands)        |
| `/sbin`   | System binaries                      |
| `/etc`    | Configuration files                  |
| `/var`    | Variable data (logs, mail, etc.)     |
| `/tmp`    | Temporary files                      |
| `/usr`    | User programs and data               |
| `/dev`    | Device files                         |
| `/proc`   | Kernel and process info (virtual FS) |

---

### 💻 **Basic Linux Commands**

Let’s start with fundamental commands every user must know.

#### 1. **`pwd` — Print Working Directory**

Shows your current directory path.

```bash
$ pwd
/home/username
```

#### 2. **`ls` — List Directory Contents**

Displays files and directories.

```bash
$ ls            # list files
$ ls -l         # long listing format
$ ls -a         # include hidden files
$ ls -lh        # human-readable file sizes
```

#### 3. **`cd` — Change Directory**

Navigates between directories.

```bash
$ cd /home       # go to /home
$ cd ~           # go to home directory
$ cd ..          # go one directory up
```

#### 4. **`clear` — Clear the Terminal Screen**

```bash
$ clear
```

#### 5. **`echo` — Display a Line of Text**

```bash
$ echo "Hello, Linux!"
Hello, Linux!
```

#### 6. **`man` — Manual Pages**

Displays help for commands.

```bash
$ man ls
```

👉 Press `q` to quit the manual.

#### 7. **`whoami` — Display Current User**

```bash
$ whoami
username
```

#### 8. **`uname` — Display System Information**

```bash
$ uname          # show OS name
$ uname -r       # show kernel version
$ uname -a       # show all details
```

#### 9. **`date` — Display or Set Date & Time**

```bash
$ date
Thu Nov  6 09:24:33 UTC 2025
```

#### 10. **`cal` — Display Calendar**

```bash
$ cal
     November 2025
Su Mo Tu We Th Fr Sa
                   1
 2  3  4  5  6  7  8
 ...
```

---

### ⚙️ **Shortcut Commands and Keyboard Tricks**

| Shortcut   | Action                              |
| ---------- | ----------------------------------- |
| `Ctrl + C` | Stop current process                |
| `Ctrl + D` | Logout / End input                  |
| `Ctrl + L` | Clear screen                        |
| `↑` / `↓`  | Command history                     |
| `Tab`      | Auto-complete filenames or commands |

---

### 🧩 **Practical Example**

Let’s simulate a basic workflow:

```bash
$ pwd
/home/student
$ mkdir test_dir
$ cd test_dir
$ echo "Linux Basics" > file1.txt
$ ls -l
-rw-r--r-- 1 student student 13 Nov  6 09:30 file1.txt
$ cat file1.txt
Linux Basics
```

---

### 💡 **Tips for Beginners**

* Use `man <command>` or `<command> --help` often.
* Tab completion saves time and prevents typos.
* Always know **where you are** (`pwd`).
* Avoid running commands as `root` unless necessary.

---

## 🎯 **Common Interview Questions — Section 1**

1. **What is Linux, and how is it different from Windows or macOS?**
   → Linux is open-source, based on UNIX, and offers better security and stability.

2. **What is the root directory in Linux?**
   → `/` — the top-most directory in the file system.

3. **How can you find out which directory you are in?**
   → `pwd` command.

4. **What does the `ls -l` command show?**
   → Lists files with permissions, ownership, and size.

5. **How can you see hidden files?**
   → Use `ls -a`.

6. **How do you get help for a command in Linux?**
   → `man <command>` or `<command> --help`.

7. **Difference between `cd ~` and `cd ..`?**
   → `cd ~` → Home directory; `cd ..` → Parent directory.

---

# 🗂️ **Section 2: File and Directory Management**

---

This section covers how to **create, view, move, copy, and delete** files and directories — the foundation of Linux system navigation and file manipulation.

---

## 🧱 **1. Creating Files**

Linux provides several commands for creating files.

### **a) `touch` — Create an Empty File or Update Timestamp**

```bash
$ touch file1.txt
```

* Creates an empty file if it doesn’t exist.
* If it exists, updates the last modified time.

Example:

```bash
$ ls -l file1.txt
-rw-r--r-- 1 user user 0 Nov 6 09:42 file1.txt
```

### **b) `echo` — Create and Write Text into File**

```bash
$ echo "This is a sample file" > file2.txt
```

* `>` overwrites file content.
* `>>` appends content to existing file.

Example:

```bash
$ echo "New line" >> file2.txt   # Append
```

### **c) `cat` — Create File with Content**

```bash
$ cat > notes.txt
Type your text here
Press Ctrl + D to save
```

---

## 📁 **2. Creating Directories**

### **`mkdir` — Make Directories**

```bash
$ mkdir my_folder
```

* To create multiple directories:

  ```bash
  $ mkdir dir1 dir2 dir3
  ```

* To create nested directories:

  ```bash
  $ mkdir -p /home/user/projects/app/config
  ```

---

## 🧭 **3. Viewing Files**

### **a) `cat` — Display File Content**

```bash
$ cat file2.txt
```

* Combine multiple files:

  ```bash
  $ cat file1.txt file2.txt > merged.txt
  ```

### **b) `tac` — Display File in Reverse**

```bash
$ tac file2.txt
```

### **c) `head` — Show First Lines of a File**

```bash
$ head -n 5 file2.txt
```

(Shows first 5 lines.)

### **d) `tail` — Show Last Lines of a File**

```bash
$ tail -n 5 file2.txt
```

* To **monitor a file live** (e.g., logs):

  ```bash
  $ tail -f /var/log/syslog
  ```

---

## 🔁 **4. Copying, Moving, and Renaming**

### **a) `cp` — Copy Files or Directories**

```bash
$ cp file1.txt /home/user/backup/
```

* Copy with verbose output:

  ```bash
  $ cp -v file1.txt backup/
  ```

* Copy entire directory (recursive):

  ```bash
  $ cp -r my_folder new_folder
  ```

### **b) `mv` — Move or Rename Files**

```bash
$ mv file1.txt /home/user/Documents/
```

* Rename file:

  ```bash
  $ mv oldname.txt newname.txt
  ```

* Move multiple files:

  ```bash
  $ mv file1.txt file2.txt target_dir/
  ```

---

## 🗑️ **5. Removing Files and Directories**

### **a) `rm` — Remove Files**

```bash
$ rm file1.txt
```

* Remove multiple:

  ```bash
  $ rm file1.txt file2.txt
  ```

* Remove with confirmation:

  ```bash
  $ rm -i file1.txt
  ```

### **b) `rmdir` — Remove Empty Directories**

```bash
$ rmdir empty_folder
```

### **c) `rm -r` — Remove Directories Recursively**

```bash
$ rm -r my_folder
```

> ⚠️ **Caution:** `rm -rf /` can delete your entire system.
> Always double-check paths before executing.

---

## 🔎 **6. Searching Files and Directories**

### **a) `find` — Search by Name, Type, Size, etc.**

```bash
$ find /home -name "file1.txt"
```

Other examples:

```bash
$ find . -type f -name "*.txt"      # Find all .txt files
$ find /var -size +10M              # Files larger than 10 MB
```

### **b) `locate` — Fast Search Using Database**

```bash
$ locate file1.txt
```

> Use `sudo updatedb` first to refresh the database.

---

## 🧮 **7. Counting Lines, Words, and Characters**

### **`wc` — Word Count Utility**

```bash
$ wc file2.txt
```

Output example:

```
3  15  90  file2.txt
# (lines, words, bytes)
```

To count only lines:

```bash
$ wc -l file2.txt
```

---

## 🧰 **8. File Comparison and Differences**

### **`diff` — Compare Two Files Line by Line**

```bash
$ diff file1.txt file2.txt
```

Shows lines that differ.
Add `-y` for side-by-side view:

```bash
$ diff -y file1.txt file2.txt
```

---

## 🧩 **9. File Compression and Archiving**

### **a) `tar` — Archive Files**

```bash
$ tar -cvf archive.tar my_folder/
```

* `c` = create
* `v` = verbose
* `f` = filename

Extract archive:

```bash
$ tar -xvf archive.tar
```

### **b) `gzip` — Compress Files**

```bash
$ gzip file1.txt
```

Decompress:

```bash
$ gunzip file1.txt.gz
```

### **c) `zip` and `unzip`**

```bash
$ zip archive.zip file1.txt file2.txt
$ unzip archive.zip
```

---

## 🧠 **Practical Example**

```bash
$ mkdir project
$ cd project
$ echo "Hello Linux" > main.txt
$ cp main.txt backup.txt
$ mv backup.txt ../
$ ls
main.txt
$ rm main.txt
$ cd ..
$ tar -cvf project_backup.tar project/
```

---

## 🧩 **Interview Questions — Section 2**

1. **How do you create an empty file in Linux?**
   → `touch filename`

2. **Difference between `rm` and `rmdir`?**
   → `rm` removes files (and directories with `-r`), `rmdir` only removes empty directories.

3. **How do you copy directories recursively?**
   → `cp -r source_dir target_dir`

4. **What is the difference between `>` and `>>`?**
   → `>` overwrites; `>>` appends.

5. **How to find all `.log` files larger than 10 MB in `/var`?**
   → `find /var -type f -name "*.log" -size +10M`

6. **How to compress and extract a directory?**
   → Compress: `tar -cvf archive.tar dir/`
   Extract: `tar -xvf archive.tar`

7. **Difference between `find` and `locate`?**
   → `find` searches in real-time; `locate` uses a database (faster but less current).

---

# 📜 **Section 3: File Viewing and Editing in Linux**

---

Text files are the **backbone of Linux** — configuration files, scripts, logs, everything is text-based.
So knowing how to **view, read, and edit** files is crucial for both users and system administrators.

---

## 🧾 **1. Viewing Files**

Let’s look at the various ways to open and inspect files without editing them.

---

### **a) `cat` — Concatenate and Display File Content**

**Syntax:**

```bash
cat [options] filename
```

**Examples:**

```bash
$ cat file.txt
$ cat file1.txt file2.txt > merged.txt  # Combine two files
```

**Common Options:**

| Option | Description                     |
| ------ | ------------------------------- |
| `-n`   | Number all lines                |
| `-b`   | Number non-empty lines          |
| `-E`   | Display `$` at end of each line |

**Example:**

```bash
$ cat -n /etc/passwd | head -5
```

---

### **b) `tac` — Display File in Reverse Order**

```bash
$ tac file.txt
```

(Displays lines starting from the end — “tac” is reverse of “cat”.)

---

### **c) `less` — View Files One Page at a Time**

**Usage:**

```bash
$ less /var/log/syslog
```

**Navigation Keys:**

| Key        | Action              |
| ---------- | ------------------- |
| `Space`    | Next page           |
| `b`        | Previous page       |
| `/pattern` | Search for a string |
| `n`        | Next search result  |
| `q`        | Quit                |

💡 *`less` is preferred over `cat` for large files since it doesn’t load the whole file at once.*

---

### **d) `more` — Similar to `less` (Older Version)**

```bash
$ more filename
```

Use `Enter` for next line, `Space` for next page, `q` to quit.

---

### **e) `head` — View First Few Lines**

```bash
$ head file.txt
```

* By default, shows first 10 lines.
* Custom number of lines:

  ```bash
  $ head -n 5 file.txt
  ```

---

### **f) `tail` — View Last Few Lines**

```bash
$ tail file.txt
```

* Shows last 10 lines by default.
* Custom lines:

  ```bash
  $ tail -n 15 file.txt
  ```

**Real-time monitoring:**

```bash
$ tail -f /var/log/syslog
```

Useful for watching log files live (e.g., when troubleshooting servers).

---

## ✏️ **2. Editing Files in Linux**

Now that we can view files, let’s learn how to **edit them**.

---

### **a) `nano` — Simple Command-Line Text Editor**

**Usage:**

```bash
$ nano filename
```

**Nano Shortcuts:**

| Shortcut   | Description |
| ---------- | ----------- |
| `Ctrl + O` | Save file   |
| `Ctrl + X` | Exit editor |
| `Ctrl + W` | Search      |
| `Ctrl + K` | Cut line    |
| `Ctrl + U` | Paste line  |
| `Ctrl + G` | Show help   |

Example:

```bash
$ nano notes.txt
```

(Type your text → `Ctrl+O` → Enter → `Ctrl+X`)

👉 Best for beginners.

---

### **b) `vi` / `vim` — Powerful Text Editor**

Vim (Vi Improved) is one of the most used editors for system admins and developers.

**To open a file:**

```bash
$ vi filename
```

#### **Vi Modes**

1. **Command Mode** – default mode when you open a file
2. **Insert Mode** – to type text
3. **Last Line Mode** – for saving and quitting

---

#### **Basic Workflow**

| Action              | Command |
| ------------------- | ------- |
| Enter Insert Mode   | `i`     |
| Exit Insert Mode    | `Esc`   |
| Save file           | `:w`    |
| Quit                | `:q`    |
| Save and Quit       | `:wq`   |
| Quit without Saving | `:q!`   |
| Delete a Line       | `dd`    |
| Copy a Line         | `yy`    |
| Paste               | `p`     |
| Undo                | `u`     |
| Search              | `/text` |

Example:

```bash
$ vi config.txt
# Press i → edit → Esc → :wq
```

💡 *Once you get comfortable, Vim becomes lightning-fast.*

---

### **c) `gedit` — GUI Text Editor (for Desktop Environments)**

```bash
$ gedit file.txt &
```

Opens a graphical text editor — convenient for Ubuntu or Fedora desktop users.

---

## 🔎 **3. Viewing File Metadata**

### **`file` — Determine File Type**

```bash
$ file /etc/passwd
/etc/passwd: ASCII text
```

### **`stat` — Display File Details**

```bash
$ stat file.txt
```

Output includes permissions, size, modification date, etc.

---

## 🧰 **4. Viewing Specific Content Inside Files**

### **`grep` — Search for Text Patterns**

```bash
$ grep "error" /var/log/syslog
```

**Common options:**

| Option    | Meaning            |
| --------- | ------------------ |
| `-i`      | Ignore case        |
| `-n`      | Show line numbers  |
| `-r`      | Search recursively |
| `--color` | Highlight matches  |

Example:

```bash
$ grep -in "failed" /var/log/auth.log
```

---

## 🧩 **5. Combining Commands**

You can combine file viewing commands using **pipes (|)**:

Example:

```bash
$ cat /var/log/syslog | grep "error" | head -10
```

Breakdown:

* `cat` — read file
* `grep "error"` — filter lines containing “error”
* `head -10` — show only first 10 results

---

## 🧠 **Practical Example**

```bash
$ cat > demo.txt
Linux is powerful.
Linux is open source.
Linux is everywhere.
<Ctrl + D>

$ grep -i "linux" demo.txt
$ head -n 2 demo.txt
$ tail -n 1 demo.txt
$ vi demo.txt   # Edit content
```

---

## 🎯 **Common Interview Questions — Section 3**

1. **How do you view the last 20 lines of a file?**
   → `tail -n 20 filename`

2. **How to monitor a log file in real time?**
   → `tail -f /var/log/syslog`

3. **What is the difference between `cat` and `less`?**
   → `cat` prints the entire file; `less` shows it page by page.

4. **How do you edit a file using Vim?**
   → Open with `vi filename`, press `i` to insert, `Esc` to exit, `:wq` to save and quit.

5. **What’s the difference between command mode and insert mode in Vim?**
   → Command mode executes operations; insert mode lets you type text.

6. **How to search for a keyword in a file using `grep`?**
   → `grep "keyword" filename`

7. **What is the use of the pipe (`|`) in Linux?**
   → It connects the output of one command to the input of another.

---

# 🔐 **Section 4: File Permissions and Ownership**

---

## 🧩 **1. Understanding Linux File Permissions**

Every file or directory in Linux has **three levels of permissions**:

| Level            | Description                           |
| ---------------- | ------------------------------------- |
| **Owner (User)** | The user who created the file         |
| **Group**        | A set of users that share permissions |
| **Others**       | Everyone else on the system           |

---

### **Three Types of Permissions**

| Permission  | Symbol | Description                                      |
| ----------- | ------ | ------------------------------------------------ |
| **Read**    | `r`    | View file contents / list directory              |
| **Write**   | `w`    | Modify file / add or remove files from directory |
| **Execute** | `x`    | Run file as a program / enter directory          |

---

### **Example:**

```bash
$ ls -l
-rwxr-xr--  1 user user  4096 Nov 6 11:00 script.sh
```

Let’s decode this:

```
- rwx r-x r--
  |   |   |
  |   |   └─ Others: read only
  |   └──── Group: read + execute
  └──────── User (owner): read + write + execute
```

The first character (`-`) shows the **type**:

* `-` → file
* `d` → directory
* `l` → symbolic link

---

## ⚙️ **2. Changing File Permissions: `chmod`**

### **Syntax:**

```bash
chmod [options] mode file
```

There are **two ways** to set permissions:

1. **Symbolic Mode**
2. **Numeric (Octal) Mode**

---

### **a) Symbolic Mode**

| Operator | Meaning              |
| -------- | -------------------- |
| `+`      | Add permission       |
| `-`      | Remove permission    |
| `=`      | Set exact permission |

Examples:

```bash
$ chmod u+x script.sh    # Add execute for user
$ chmod g-w file.txt     # Remove write for group
$ chmod o+r file.txt     # Add read for others
$ chmod u=rwx,g=rx,o=r   # Full control for user, limited for others
```

---

### **b) Numeric (Octal) Mode**

Each permission type is represented by a number:

| Permission  | Value |
| ----------- | ----- |
| Read (r)    | 4     |
| Write (w)   | 2     |
| Execute (x) | 1     |

Add them together for each category:

| Role   | Example     | Value |
| ------ | ----------- | ----- |
| Owner  | rwx = 4+2+1 | 7     |
| Group  | r-x = 4+0+1 | 5     |
| Others | r-- = 4+0+0 | 4     |

So:

```bash
$ chmod 754 script.sh
```

Means:

```
Owner: rwx (7)
Group: r-x (5)
Others: r-- (4)
```

---

### **Common Permission Settings**

| Mode  | Meaning                                                       |
| ----- | ------------------------------------------------------------- |
| `777` | Full access to everyone (not safe)                            |
| `755` | Owner: all; Group/Others: read + execute (common for scripts) |
| `644` | Owner: read/write; others: read only (default for text files) |
| `700` | Only owner can access (secure private files)                  |

---

## 👑 **3. File Ownership**

Every file has:

* **Owner (User)** → who created it
* **Group** → users with shared access

View ownership:

```bash
$ ls -l
-rw-r--r-- 1 alice developers 1024 Nov 6 11:00 app.conf
```

Here:

* Owner = `alice`
* Group = `developers`

---

### **Changing Ownership**

#### **a) `chown` — Change File Owner**

```bash
$ sudo chown bob file.txt
```

Changes owner to `bob`.

To change both owner and group:

```bash
$ sudo chown bob:developers file.txt
```

Change recursively (for directories):

```bash
$ sudo chown -R bob:developers /opt/project/
```

---

#### **b) `chgrp` — Change Group Ownership**

```bash
$ sudo chgrp developers file.txt
```

---

## 🧱 **4. Directory Permissions**

For **directories**, permissions work slightly differently:

| Permission | Description                                        |
| ---------- | -------------------------------------------------- |
| `r`        | Allows listing of directory contents (`ls`)        |
| `w`        | Allows creating or deleting files in the directory |
| `x`        | Allows entering the directory (`cd`)               |

Example:

```bash
$ chmod 755 mydir
```

* Owner: full access
* Group/Others: can enter and read

---

## 🔐 **5. Special Permissions**

There are **three advanced permission bits** used mainly in system administration.

| Special Bit    | Symbol      | Numeric | Description                               |
| -------------- | ----------- | ------- | ----------------------------------------- |
| **SetUID**     | `s` (user)  | 4       | Run program with file owner’s privileges  |
| **SetGID**     | `s` (group) | 2       | New files inherit directory’s group       |
| **Sticky Bit** | `t`         | 1       | Only owner can delete files in shared dir |

---

### **a) SetUID Example**

```bash
$ chmod 4755 /usr/bin/passwd
```

Allows normal users to run `passwd` (which changes passwords) with root privileges.

---

### **b) SetGID Example**

```bash
$ chmod 2755 /shared/folder
```

Any new files inside `/shared/folder` will inherit the folder’s group.

---

### **c) Sticky Bit Example**

```bash
$ chmod +t /tmp
```

Prevents users from deleting others’ files in `/tmp`.
(You can verify it as `drwxrwxrwt`.)

---

## 🧰 **6. Viewing Permission in Octal Format**

```bash
$ stat -c "%A %a %n" file.txt
-rw-r--r-- 644 file.txt
```

Displays symbolic and numeric permission in one go.

---

## 🧠 **Practical Example**

```bash
$ touch myscript.sh
$ chmod 700 myscript.sh
$ ls -l myscript.sh
-rwx------ 1 user user 0 Nov 6 11:30 myscript.sh

$ sudo chown root:root myscript.sh
$ ls -l myscript.sh
-rwx------ 1 root root 0 Nov 6 11:30 myscript.sh
```

---

## 🎯 **Common Interview Questions — Section 4**

1. **What command changes file permissions?**
   → `chmod`

2. **Explain the difference between symbolic and numeric mode in chmod.**
   → Symbolic uses letters (u, g, o); numeric uses octal numbers (e.g., 755).

3. **What does 755 mean?**
   → Owner: rwx; Group: r-x; Others: r-x.

4. **How do you change file owner and group in one command?**
   → `chown user:group filename`

5. **What is the difference between SetUID and SetGID?**
   → SetUID runs program with owner’s privileges; SetGID applies group inheritance.

6. **What is the Sticky Bit used for?**
   → Prevents users from deleting others’ files in shared directories like `/tmp`.

7. **How do directory permissions differ from file permissions?**
   → `x` means “enter directory” instead of “execute”.

8. **How to give only read and execute permission to everyone?**
   → `chmod 555 filename`

---

# ⚙️ **Section 5: Process Management in Linux**

---

Managing processes effectively is a core Linux skill — whether you’re troubleshooting performance issues, controlling services, or handling background jobs.

Let’s learn everything from the basics to advanced process control.

---

## 🧩 **1. What is a Process?**

A **process** is a program in execution.
Every command you run starts a process, which is assigned a **PID (Process ID)** — a unique number used to identify it.

You can check all running processes using commands like `ps`, `top`, and `pgrep`.

---

## 🧠 **2. Viewing Processes**

### **a) `ps` — Process Status**

**Basic usage:**

```bash
$ ps
```

Shows processes running in the current shell.

Example:

```
PID   TTY          TIME CMD
1234  pts/0    00:00:00 bash
1289  pts/0    00:00:00 ps
```

---

### **b) Common Options**

| Option             | Description                               |
| ------------------ | ----------------------------------------- |
| `ps -e` or `ps -A` | Show all processes                        |
| `ps -u username`   | Show processes of a specific user         |
| `ps -f`            | Full-format listing                       |
| `ps -ef`           | System-wide detailed list                 |
| `ps aux`           | Show processes from all users (BSD style) |

**Example:**

```bash
$ ps -ef | grep ssh
root     1001  1  0 09:30 ?  00:00:00 /usr/sbin/sshd
```

---

### **c) `pgrep` — Find Process by Name**

```bash
$ pgrep nginx
```

Shows PID(s) of matching processes.

---

### **d) `pidof` — Find Process ID of a Running Program**

```bash
$ pidof systemd
```

---

## 🧮 **3. Real-Time Process Monitoring**

### **a) `top` — Dynamic Real-Time View**

```bash
$ top
```

Displays system summary + list of active processes.

**Common keys inside `top`:**

| Key | Action                     |
| --- | -------------------------- |
| `P` | Sort by CPU usage          |
| `M` | Sort by memory usage       |
| `k` | Kill a process (enter PID) |
| `q` | Quit                       |
| `h` | Help                       |

---

### **b) `htop` — Interactive Process Viewer (Better `top`)**

```bash
$ htop
```

* Colorful, scrollable interface
* Allows interactive process management (F9 = kill, F6 = sort)

> Install if missing:
>
> ```bash
> sudo apt install htop    # Debian/Ubuntu
> sudo yum install htop    # RHEL/CentOS
> ```

---

## 🧰 **4. Managing Processes**

### **a) `kill` — Terminate a Process**

```bash
$ kill <PID>
```

Example:

```bash
$ kill 1234
```

If a process refuses to stop, use **force kill**:

```bash
$ kill -9 1234
```

---

### **b) `pkill` — Kill Process by Name**

```bash
$ pkill firefox
```

Kills all processes matching the name “firefox”.

---

### **c) `killall` — Kill All Instances of a Command**

```bash
$ killall nginx
```

---

### **d) Signals in Linux (for `kill`)**

| Signal    | Number | Meaning                        |
| --------- | ------ | ------------------------------ |
| `SIGTERM` | 15     | Terminate gracefully (default) |
| `SIGKILL` | 9      | Force kill immediately         |
| `SIGHUP`  | 1      | Reload configuration           |
| `SIGSTOP` | 19     | Pause a process                |
| `SIGCONT` | 18     | Resume a stopped process       |

Example:

```bash
$ kill -STOP 2345   # Pause
$ kill -CONT 2345   # Resume
```

---

## 🧱 **5. Background and Foreground Processes**

### **a) Running in Background**

Add `&` at the end of a command:

```bash
$ long_task.sh &
```

The shell will show a job number and PID:

```
[1] 2456
```

---

### **b) Listing Background Jobs**

```bash
$ jobs
```

Example:

```
[1]+  Running  long_task.sh &
```

---

### **c) Bringing Job to Foreground**

```bash
$ fg %1
```

(Brings job number 1 to the foreground.)

---

### **d) Sending Foreground Job to Background**

Press **Ctrl + Z** → suspends the process.
Then type:

```bash
$ bg
```

Resumes it in the background.

---

## ⚖️ **6. Process Priority and Scheduling**

### **a) `nice` — Start Process with a Priority**

Every process has a **nice value** from **-20 (highest priority)** to **19 (lowest priority)**.
By default, processes start with `0`.

```bash
$ nice -n 10 myscript.sh &
```

---

### **b) `renice` — Change Priority of Running Process**

```bash
$ renice -n -5 -p 2345
```

Changes priority of PID 2345 to **-5** (higher priority).

---

## 🕒 **7. Monitoring System and Resource Usage**

### **a) `uptime` — Show System Load and Running Time**

```bash
$ uptime
 11:45:22 up 3 days,  4:22,  2 users,  load average: 0.25, 0.35, 0.45
```

---

### **b) `free` — Show Memory Usage**

```bash
$ free -h
```

---

### **c) `vmstat` — Virtual Memory Statistics**

```bash
$ vmstat 2 5
```

Shows memory, swap, I/O, and CPU usage every 2 seconds for 5 times.

---

### **d) `lsof` — List Open Files**

```bash
$ lsof -p 1234
```

Lists all files opened by process 1234.

---

## 🧩 **8. Managing System Services**

Modern Linux systems use **systemd** for managing services.

### **a) List All Services**

```bash
$ systemctl list-units --type=service
```

### **b) Start/Stop/Restart a Service**

```bash
$ sudo systemctl start nginx
$ sudo systemctl stop nginx
$ sudo systemctl restart nginx
```

### **c) Enable/Disable Service at Boot**

```bash
$ sudo systemctl enable nginx
$ sudo systemctl disable nginx
```

### **d) Check Service Status**

```bash
$ systemctl status nginx
```

---

## 🧠 **Practical Example**

```bash
$ ps -ef | grep python
$ kill 3045
$ nice -n 10 ./backup.sh &
$ top
$ systemctl restart ssh
```

---

## 🎯 **Common Interview Questions — Section 5**

1. **What is a process ID (PID)?**
   → A unique number assigned to every running process.

2. **Difference between `ps` and `top`?**
   → `ps` gives a snapshot; `top` provides real-time updates.

3. **How to kill a process by name?**
   → `pkill processname` or `killall processname`

4. **What does the `kill -9` command do?**
   → Forcefully terminates the process (SIGKILL).

5. **How to list background jobs?**
   → `jobs`

6. **What is the difference between foreground and background processes?**
   → Foreground occupies the terminal; background runs independently.

7. **What is a “nice value”?**
   → Determines process priority (-20 high, +19 low).

8. **How to check if a service is running in Linux?**
   → `systemctl status servicename`

9. **How to restart a service using systemd?**
   → `sudo systemctl restart servicename`

10. **What is the use of the `lsof` command?**
    → Lists files opened by a process.

---

# 📦 **Section 6: Package Management in Linux**

---

Every Linux distribution (distro) uses a **package manager** to install, update, and remove software.
Understanding how these systems work is crucial for **system administration, DevOps, and troubleshooting**.

---

## 🧩 **1. What Is a Package Manager?**

A **package** in Linux is a collection of files (binaries, configs, documentation) bundled for installation.
A **package manager** automates:

* Installing software
* Removing software
* Updating packages
* Managing dependencies

---

### **Package Manager Types (by Distro)**

| Distro Family              | Tool             | Low-Level Tool |
| -------------------------- | ---------------- | -------------- |
| **Debian / Ubuntu / Mint** | `apt`, `apt-get` | `dpkg`         |
| **RHEL / CentOS / Fedora** | `yum`, `dnf`     | `rpm`          |
| **Arch Linux**             | `pacman`         | —              |
| **openSUSE**               | `zypper`         | `rpm`          |

---

## 🧱 **2. Debian/Ubuntu Package Management**

We’ll start with the most common: **APT (Advanced Package Tool)**.

---

### **a) Updating Package Lists**

```bash
$ sudo apt update
```

Refreshes package information from repositories.

---

### **b) Upgrading Installed Packages**

```bash
$ sudo apt upgrade
```

Upgrades all installed packages to latest versions.

For full system upgrade (may remove obsolete ones):

```bash
$ sudo apt full-upgrade
```

---

### **c) Installing a Package**

```bash
$ sudo apt install package_name
```

Example:

```bash
$ sudo apt install nginx
```

---

### **d) Removing a Package**

* Remove but keep config files:

  ```bash
  $ sudo apt remove nginx
  ```
* Remove including config files:

  ```bash
  $ sudo apt purge nginx
  ```

---

### **e) Listing and Searching Packages**

* List installed packages:

  ```bash
  $ apt list --installed
  ```

* Search for a package:

  ```bash
  $ apt search nginx
  ```

* Show package details:

  ```bash
  $ apt show nginx
  ```

---

### **f) Cleaning Up**

```bash
$ sudo apt autoremove
```

Removes unused dependencies.

```bash
$ sudo apt clean
```

Cleans cached `.deb` files.

---

## ⚙️ **3. Using dpkg (Low-Level Tool for Debian)**

APT depends on `dpkg`, but `dpkg` can be used directly for local `.deb` files.

### **a) Install a .deb File**

```bash
$ sudo dpkg -i package.deb
```

If dependencies are missing:

```bash
$ sudo apt -f install
```

### **b) Remove a Package**

```bash
$ sudo dpkg -r packagename
```

### **c) List Installed Packages**

```bash
$ dpkg -l
```

### **d) Find Package That Owns a File**

```bash
$ dpkg -S /usr/bin/python3
```

---

## 🧰 **4. RHEL/CentOS/Fedora Package Management**

Red Hat-based systems use **YUM** or **DNF** (modern replacement for YUM).

---

### **a) Updating System Repositories**

```bash
$ sudo yum check-update
```

or (for Fedora / newer distros):

```bash
$ sudo dnf check-update
```

---

### **b) Installing a Package**

```bash
$ sudo yum install httpd
```

or

```bash
$ sudo dnf install httpd
```

---

### **c) Removing a Package**

```bash
$ sudo yum remove httpd
```

---

### **d) Searching for Packages**

```bash
$ yum search nginx
```

---

### **e) Show Package Information**

```bash
$ yum info nginx
```

---

### **f) Listing Packages**

```bash
$ yum list installed
```

---

### **g) Cleaning Cache**

```bash
$ sudo yum clean all
```

---

## ⚙️ **5. Using rpm (Low-Level Tool for RHEL)**

`rpm` is similar to `dpkg` — it installs `.rpm` packages.

### **a) Install a .rpm File**

```bash
$ sudo rpm -ivh package.rpm
```

Options:

* `-i` = install
* `-v` = verbose
* `-h` = show progress (hash marks)

### **b) Remove a Package**

```bash
$ sudo rpm -e packagename
```

### **c) Query Packages**

```bash
$ rpm -qa | grep nginx
```

### **d) Verify Package**

```bash
$ rpm -V packagename
```

### **e) Find Package for File**

```bash
$ rpm -qf /usr/bin/ls
```

---

## 🧮 **6. Repository Management**

### **a) Adding Repositories (Debian/Ubuntu)**

Edit `/etc/apt/sources.list` or add files under `/etc/apt/sources.list.d/`.

Example:

```bash
$ sudo add-apt-repository ppa:deadsnakes/ppa
$ sudo apt update
```

---

### **b) Adding Repositories (RHEL/Fedora)**

Add `.repo` file under `/etc/yum.repos.d/`.

Example:

```bash
$ sudo dnf config-manager --add-repo=https://nginx.org/packages/mainline/centos/8/x86_64/
```

---

## 🧩 **7. Working with Software Groups**

YUM and DNF allow installing “groups” of software:

```bash
$ sudo yum groupinstall "Development Tools"
```

List available groups:

```bash
$ yum group list
```

---

## 🧠 **8. Installing Software from Source (Manual)**

Sometimes, you’ll need to build a package from source code:

```bash
$ tar -xvf software.tar.gz
$ cd software/
$ ./configure
$ make
$ sudo make install
```

> ⚠️ Requires development tools (`gcc`, `make`, `build-essential`, etc.)

---

## 🔍 **9. Verifying and Managing Dependencies**

### **Check Dependencies of a Package**

```bash
$ apt-cache depends nginx
```

### **Check Reverse Dependencies**

```bash
$ apt-cache rdepends nginx
```

---

## 🧠 **Practical Example**

```bash
$ sudo apt update
$ sudo apt install vim
$ vim --version
$ sudo apt remove vim
$ sudo apt autoremove
```

For RHEL:

```bash
$ sudo yum install tree
$ tree /etc
$ sudo yum remove tree
```

---

## 🎯 **Common Interview Questions — Section 6**

1. **What is the difference between `apt` and `dpkg`?**
   → `apt` handles dependencies and repositories; `dpkg` only manages individual `.deb` files.

2. **How do you install a package in Debian vs RHEL?**
   → Debian: `apt install`; RHEL: `yum install`.

3. **How do you remove a package along with its configuration files?**
   → `sudo apt purge packagename`

4. **What is the command to update all packages?**
   → `sudo apt upgrade` (Debian) or `sudo yum update` (RHEL)

5. **What is the difference between `yum` and `dnf`?**
   → `dnf` is the newer, faster version of `yum` with better dependency resolution.

6. **How do you find which package installed a specific file?**
   → Debian: `dpkg -S /path/to/file`
   RHEL: `rpm -qf /path/to/file`

7. **What is a repository?**
   → A central location where packages are stored and fetched from for installation.

8. **How can you clean up unused packages in Ubuntu?**
   → `sudo apt autoremove` and `sudo apt clean`

---

# 👥 **Section 7: User and Group Management in Linux**

---

This section will teach you how to create, delete, and manage users and groups, set passwords, configure access, and understand related system files — all **crucial for security and system management**.

---

## 🧩 **1. Understanding Users and Groups**

### 🧍‍♂️ **User**

A user represents a **person or process** that can log in or run applications.

Each user has:

* A **username**
* A **UID (User ID)**
* A **home directory**
* A **default shell**

### 👥 **Group**

A group is a **collection of users** that share certain permissions.

Each user:

* Belongs to **one primary group**
* May be a member of **additional (secondary) groups**

---

## 📂 **2. Important Files for User Management**

| File           | Description                                                       |
| -------------- | ----------------------------------------------------------------- |
| `/etc/passwd`  | Stores basic user info (username, UID, GID, home dir, shell)      |
| `/etc/shadow`  | Stores encrypted passwords and aging info (only readable by root) |
| `/etc/group`   | Stores group info (group name, GID, members)                      |
| `/etc/gshadow` | Stores encrypted group passwords                                  |

---

### 🔍 **Example of `/etc/passwd` Entry**

```
alice:x:1001:1001:Alice Doe:/home/alice:/bin/bash
```

Breakdown:

| Field         | Meaning                                            |
| ------------- | -------------------------------------------------- |
| `alice`       | Username                                           |
| `x`           | Placeholder for password (stored in `/etc/shadow`) |
| `1001`        | UID (User ID)                                      |
| `1001`        | GID (Group ID)                                     |
| `Alice Doe`   | User description                                   |
| `/home/alice` | Home directory                                     |
| `/bin/bash`   | Login shell                                        |

---

## 👤 **3. Creating and Managing Users**

### **a) Add a New User**

```bash
$ sudo useradd username
```

This creates a user but may not create a home directory automatically (depends on distro).

**To ensure home directory and default shell:**

```bash
$ sudo useradd -m -s /bin/bash username
```

**Options:**

| Option | Description               |
| ------ | ------------------------- |
| `-m`   | Create home directory     |
| `-s`   | Specify login shell       |
| `-c`   | Add comment (description) |
| `-u`   | Assign specific UID       |
| `-g`   | Set primary group         |

Example:

```bash
$ sudo useradd -m -s /bin/bash -c "Dev User" devuser
```

---

### **b) Set Password for User**

```bash
$ sudo passwd username
```

You’ll be prompted to enter a new password.

---

### **c) Delete a User**

* Delete user only:

  ```bash
  $ sudo userdel username
  ```
* Delete user **and home directory**:

  ```bash
  $ sudo userdel -r username
  ```

---

### **d) Modify Existing User**

```bash
$ sudo usermod [options] username
```

**Common Options:**

| Option             | Description                           |
| ------------------ | ------------------------------------- |
| `-l newname`       | Change username                       |
| `-d /new/home`     | Change home directory                 |
| `-s /bin/zsh`      | Change shell                          |
| `-G group1,group2` | Add to secondary groups               |
| `-aG`              | Append groups without removing others |

**Example:**

```bash
$ sudo usermod -aG sudo alice
```

→ Adds user `alice` to the `sudo` group.

---

### **e) Lock/Unlock User Account**

```bash
$ sudo passwd -l username   # Lock account
$ sudo passwd -u username   # Unlock account
```

---

## 👥 **4. Group Management**

### **a) Add a New Group**

```bash
$ sudo groupadd developers
```

### **b) Delete a Group**

```bash
$ sudo groupdel developers
```

### **c) Add User to a Group**

```bash
$ sudo usermod -aG developers alice
```

### **d) View Group Memberships**

```bash
$ groups alice
```

### **e) Change User’s Primary Group**

```bash
$ sudo usermod -g developers alice
```

---

## 🔐 **5. The Root User and Sudo Privileges**

### **Root User**

* UID = 0
* Has **unrestricted access** to the system.
* Use with caution!

Switch to root:

```bash
$ sudo su
```

Exit:

```bash
# exit
```

---

### **Sudo (Superuser Do)**

Allows normal users to run specific commands as root.

Example:

```bash
$ sudo apt update
```

Add user to sudoers:

```bash
$ sudo usermod -aG sudo username
```

Alternatively, edit the sudoers file (with care!):

```bash
$ sudo visudo
```

Add a line:

```
username ALL=(ALL:ALL) ALL
```

---

## 🧱 **6. User Password and Aging Policies**

### **a) View Password Info**

```bash
$ sudo chage -l username
```

Shows:

* Password last changed
* Expiry date
* Minimum/maximum age

---

### **b) Set Password Expiry**

```bash
$ sudo chage -M 60 username    # Password expires in 60 days
$ sudo chage -W 7 username     # Warn 7 days before expiry
```

---

## 🧮 **7. Switch Users**

### **a) Using `su`**

```bash
$ su username
```

Switches to another user (you’ll be prompted for their password).

Return to your account:

```bash
$ exit
```

### **b) Using `sudo su`**

```bash
$ sudo su - username
```

Switches user with root privileges (requires your own sudo password).

---

## 🧠 **8. View Current and Logged-In Users**

| Command           | Description                                    |
| ----------------- | ---------------------------------------------- |
| `whoami`          | Displays current username                      |
| `who`             | Shows all logged-in users                      |
| `w`               | Displays active users and their processes      |
| `id`              | Shows UID, GID, and groups of current user     |
| `last`            | Shows login history                            |
| `finger username` | Shows user details (requires `finger` package) |

Example:

```bash
$ id alice
uid=1001(alice) gid=1001(alice) groups=1001(alice),27(sudo)
```

---

## 🧩 **9. Default Configuration Files**

| File              | Description                                                                    |
| ----------------- | ------------------------------------------------------------------------------ |
| `/etc/skel/`      | Template for new user’s home directory (contains default files like `.bashrc`) |
| `/etc/login.defs` | Defines default UID/GID range, password expiry policies                        |
| `/etc/sudoers`    | Controls user sudo access                                                      |

---

## 🧠 **Practical Example**

```bash
$ sudo groupadd testers
$ sudo useradd -m -s /bin/bash -G testers dev1
$ sudo passwd dev1
$ id dev1
$ groups dev1
$ sudo chage -M 45 dev1
$ sudo userdel -r dev1
```

---

## 🎯 **Common Interview Questions — Section 7**

1. **What is the difference between `useradd` and `adduser`?**
   → `adduser` is a friendlier interactive script (Debian-based); `useradd` is a low-level binary.

2. **Where are user account details stored?**
   → `/etc/passwd`

3. **What file stores encrypted passwords?**
   → `/etc/shadow`

4. **How do you change a user’s login shell?**
   → `sudo usermod -s /bin/zsh username`

5. **What command adds a user to multiple groups?**
   → `sudo usermod -aG group1,group2 username`

6. **How do you check which groups a user belongs to?**
   → `groups username` or `id username`

7. **What does UID 0 represent?**
   → Root user (superuser).

8. **How do you expire a user’s password immediately?**
   → `sudo passwd -e username`

9. **How do you list all logged-in users?**
   → `who` or `w`

10. **What’s the difference between `su` and `sudo`?**
    → `su` switches user context and needs target user’s password;
    `sudo` runs commands as another user using your own credentials.

---

# 🌐 **Section 8: Networking Commands in Linux**

---

Networking is the backbone of servers and communication between systems.
This section covers **IP configuration, DNS, routing, connectivity testing, file transfers, and SSH access** — everything you need to manage and troubleshoot Linux networking.

---

## 🧩 **1. Viewing and Configuring Network Information**

### **a) `ifconfig` (Old Command)**

Shows or configures IP addresses of network interfaces.

```bash
$ ifconfig
```

Example output:

```
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.10  netmask 255.255.255.0  broadcast 192.168.1.255
```

> ⚠️ `ifconfig` is deprecated — replaced by `ip` command (below).

---

### **b) `ip` Command (Modern Alternative)**

**View network interfaces:**

```bash
$ ip addr show
```

or shorter:

```bash
$ ip a
```

**Assign a new IP address:**

```bash
$ sudo ip addr add 192.168.1.20/24 dev eth0
```

**Remove an IP address:**

```bash
$ sudo ip addr del 192.168.1.20/24 dev eth0
```

**Bring interface up/down:**

```bash
$ sudo ip link set eth0 up
$ sudo ip link set eth0 down
```

---

## 🌍 **2. Hostname and DNS Configuration**

### **a) Check Hostname**

```bash
$ hostname
```

### **b) Change Hostname Temporarily**

```bash
$ sudo hostname newname
```

### **c) Change Hostname Permanently**

Edit:

```bash
$ sudo hostnamectl set-hostname newname
```

### **d) Check DNS Resolution**

```bash
$ cat /etc/resolv.conf
```

Shows DNS servers.

---

## 🔍 **3. Connectivity and Testing Commands**

### **a) `ping` — Test Network Connectivity**

```bash
$ ping google.com
```

Send a fixed number of packets:

```bash
$ ping -c 5 google.com
```

---

### **b) `traceroute` — Show Route Taken by Packets**

```bash
$ traceroute google.com
```

> If not installed: `sudo apt install traceroute` or `sudo yum install traceroute`

---

### **c) `mtr` — Real-Time Traceroute with Statistics**

```bash
$ mtr google.com
```

> Combine `ping` + `traceroute` in one tool.

---

### **d) `netstat` — Display Network Connections**

```bash
$ netstat -tuln
```

Options:

| Option | Meaning                |
| ------ | ---------------------- |
| `-t`   | TCP connections        |
| `-u`   | UDP connections        |
| `-l`   | Listening ports        |
| `-n`   | Show numeric addresses |
| `-p`   | Show PID/program name  |

> Example:

```bash
$ sudo netstat -tulnp
```

---

### **e) `ss` — Modern Replacement for netstat**

```bash
$ ss -tuln
```

Lists open ports and listening sockets.

Example:

```
Netid  State  Local Address:Port  Peer Address:Port  Process
tcp    LISTEN 0.0.0.0:22         0.0.0.0:*          users:(("sshd",pid=1125,fd=3))
```

---

### **f) `nslookup` — DNS Lookup Tool**

```bash
$ nslookup google.com
```

---

### **g) `dig` — Detailed DNS Query**

```bash
$ dig google.com
```

Shows query time, server used, and DNS record details.

---

### **h) `curl` — Transfer Data from/To a Server**

```bash
$ curl https://example.com
```

To test headers:

```bash
$ curl -I https://example.com
```

Download file:

```bash
$ curl -O https://example.com/file.zip
```

---

### **i) `wget` — Download Files from Web**

```bash
$ wget https://example.com/file.zip
```

Resume interrupted download:

```bash
$ wget -c https://example.com/file.zip
```

---

## 🕸️ **4. Network Interface and Routing**

### **a) Show Routing Table**

```bash
$ route -n
```

or modern:

```bash
$ ip route show
```

**Example Output:**

```
default via 192.168.1.1 dev eth0
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.10
```

---

### **b) Add/Remove Static Routes**

**Add:**

```bash
$ sudo ip route add 10.10.10.0/24 via 192.168.1.1
```

**Delete:**

```bash
$ sudo ip route del 10.10.10.0/24
```

---

## 🔒 **5. SSH and Secure Copy**

### **a) SSH (Secure Shell)**

Connect to remote Linux machine:

```bash
$ ssh user@remote_host
```

Specify port:

```bash
$ ssh -p 2222 user@remote_host
```

---

### **b) Copy Files Securely (SCP)**

**Copy file to remote:**

```bash
$ scp file.txt user@remote:/home/user/
```

**Copy directory recursively:**

```bash
$ scp -r /local/dir user@remote:/home/user/
```

**Copy file from remote to local:**

```bash
$ scp user@remote:/home/user/file.txt .
```

---

### **c) `rsync` — Efficient File Synchronization**

```bash
$ rsync -avz file.txt user@remote:/backup/
```

Options:

| Option | Meaning                              |
| ------ | ------------------------------------ |
| `-a`   | Archive mode (preserves permissions) |
| `-v`   | Verbose                              |
| `-z`   | Compress during transfer             |

---

## 🧮 **6. Network Interface and Port Troubleshooting**

### **a) `ip link` — Show Link Layer Info**

```bash
$ ip link show
```

### **b) Check Active Ports**

```bash
$ ss -tulnp
```

### **c) Check Which Process Is Using a Port**

```bash
$ sudo lsof -i :80
```

---

### **d) Test Port Connectivity**

```bash
$ nc -zv 192.168.1.1 22
```

> Checks if port 22 is open on the remote host.

---

### **e) Check Public IP Address**

```bash
$ curl ifconfig.me
```

or

```bash
$ wget -qO- ifconfig.me
```

---

## 🧠 **7. Networking System Files**

| File                              | Description                                |
| --------------------------------- | ------------------------------------------ |
| `/etc/hosts`                      | Maps hostnames to IPs (local DNS override) |
| `/etc/hostname`                   | Defines system hostname                    |
| `/etc/resolv.conf`                | DNS server configuration                   |
| `/etc/network/interfaces`         | Interface configuration (Debian)           |
| `/etc/sysconfig/network-scripts/` | Interface config (RHEL/CentOS)             |

---

## 🧠 **Practical Example**

```bash
$ ip a
$ ping -c 4 google.com
$ traceroute 8.8.8.8
$ ss -tulnp
$ sudo systemctl restart networking
$ ssh admin@192.168.1.10
$ scp report.txt admin@192.168.1.10:/home/admin/
```

---

## 🎯 **Common Interview Questions — Section 8**

1. **How to check IP address of a system?**
   → `ip a` or `ifconfig`

2. **What command tests connectivity to another host?**
   → `ping hostname_or_ip`

3. **Difference between `netstat` and `ss`?**
   → `ss` is newer, faster, and shows more socket details.

4. **How to display the routing table?**
   → `ip route show` or `route -n`

5. **How to find which process is using port 80?**
   → `sudo lsof -i :80`

6. **How to check DNS resolution manually?**
   → `nslookup` or `dig`

7. **What is the difference between `scp` and `rsync`?**
   → `scp` copies files; `rsync` syncs efficiently with resume and differential updates.

8. **How to check your public IP address from CLI?**
   → `curl ifconfig.me`

9. **What file contains local hostname-to-IP mappings?**
   → `/etc/hosts`

10. **How to test if a remote port is open?**
    → `nc -zv IP port` (using Netcat)

---

# 🧾 **Section 9: File Permissions and Ownership in Linux**

---

Everything in Linux — from files and directories to devices and processes — has **permissions and ownerships** that control **who can read, modify, or execute** them.

Understanding these is essential for:

* System administration 🧠
* Security hardening 🔒
* File management 🧱
* Interview success 🎯

---

## 🧩 **1. File Ownership Overview**

Every file and directory in Linux is owned by:

* A **user (owner)**
* A **group**

Each ownership controls **three types of access permissions**:

1. **Read (r)**
2. **Write (w)**
3. **Execute (x)**

---

### **Example:**

```bash
$ ls -l
-rwxr-xr-- 1 alice devs  5120 Nov  6 10:30 script.sh
```

Breakdown:

| Field         | Meaning                 |
| ------------- | ----------------------- |
| `-rwxr-xr--`  | File type + permissions |
| `1`           | Link count              |
| `alice`       | Owner                   |
| `devs`        | Group                   |
| `5120`        | File size               |
| `Nov 6 10:30` | Last modified date      |
| `script.sh`   | Filename                |

---

## 🧱 **2. Permission Structure Explained**

The **permission string** has **10 characters**:

```
-rwxr-xr--
```

| Position | Description        | Example                                 |
| -------- | ------------------ | --------------------------------------- |
| 1        | File type          | `-` = file, `d` = directory, `l` = link |
| 2–4      | Owner permissions  | `rwx`                                   |
| 5–7      | Group permissions  | `r-x`                                   |
| 8–10     | Others permissions | `r--`                                   |

---

### **Permission Meanings**

| Permission | Symbol | File Meaning     | Directory Meaning       |
| ---------- | ------ | ---------------- | ----------------------- |
| Read       | `r`    | View content     | List directory contents |
| Write      | `w`    | Modify content   | Create/delete files     |
| Execute    | `x`    | Run as a program | Enter (`cd`) directory  |

---

## 🔢 **3. Numeric (Octal) Representation of Permissions**

Permissions can also be represented using numbers:

| Permission | Symbol | Value |
| ---------- | ------ | ----- |
| Read       | r      | 4     |
| Write      | w      | 2     |
| Execute    | x      | 1     |

Combine them for each user/group/others.

| Permission Set | Symbol | Value |
| -------------- | ------ | ----- |
| `rwx`          | 4+2+1  | 7     |
| `rw-`          | 4+2    | 6     |
| `r--`          | 4      | 4     |
| `---`          | 0      | 0     |

---

### **Example:**

```bash
$ chmod 754 file.txt
```

Means:

* Owner → 7 (rwx)
* Group → 5 (r-x)
* Others → 4 (r--)

Result:

```
-rwxr-xr--
```

---

## 🧰 **4. Changing Permissions — `chmod`**

### **a) Using Numeric Mode**

```bash
$ chmod 644 file.txt
```

(Owner can read/write; group and others can read.)

---

### **b) Using Symbolic Mode**

| Symbol | Meaning     |
| ------ | ----------- |
| `u`    | User/owner  |
| `g`    | Group       |
| `o`    | Others      |
| `a`    | All (u+g+o) |

Operators:

| Operator | Meaning              |
| -------- | -------------------- |
| `+`      | Add permission       |
| `-`      | Remove permission    |
| `=`      | Set exact permission |

**Examples:**

```bash
$ chmod u+x script.sh      # Add execute permission to user
$ chmod g-w file.txt       # Remove write from group
$ chmod a=r file.txt       # Everyone can only read
$ chmod ug+r file.txt      # Add read for user and group
```

---

## 👤 **5. Changing Ownership — `chown`**

**Syntax:**

```bash
$ sudo chown user:group filename
```

**Examples:**

```bash
$ sudo chown bob:bob file.txt
$ sudo chown alice:devs project/
```

**Change ownership recursively:**

```bash
$ sudo chown -R alice:devs /var/www
```

---

## 👥 **6. Changing Group Ownership — `chgrp`**

```bash
$ sudo chgrp devs file.txt
```

Recursive:

```bash
$ sudo chgrp -R admins /opt/
```

---

## 🔐 **7. Special Permissions**

Linux has **three special bits** beyond normal permissions:

### **a) SUID (Set User ID)** — `s`

When set on executables, the program runs **with the owner’s privileges**.

Example:

```bash
$ chmod u+s /usr/bin/passwd
```

`passwd` runs as root to change passwords.

View:

```
-rwsr-xr-x 1 root root 54256 /usr/bin/passwd
```

---

### **b) SGID (Set Group ID)** — `s`

When set on directories, **new files inherit the group** of the directory.

Example:

```bash
$ chmod g+s /shared
```

View:

```
drwxr-sr-x 2 root devs 4096 /shared
```

---

### **c) Sticky Bit** — `t`

Applied to directories — users can only delete their own files.

Common on `/tmp`:

```
drwxrwxrwt 10 root root 4096 /tmp
```

Set sticky bit:

```bash
$ chmod +t /data
```

---

### **Special Bits Numeric Values**

| Special Bit | Octal Value | Example           |
| ----------- | ----------- | ----------------- |
| SUID        | 4xxx        | `chmod 4755 file` |
| SGID        | 2xxx        | `chmod 2755 dir`  |
| Sticky Bit  | 1xxx        | `chmod 1755 dir`  |

---

## 🧠 **8. Viewing File Permissions and Ownership**

### **a) Using `ls -l`**

```bash
$ ls -l file.txt
```

### **b) Using `stat`**

```bash
$ stat file.txt
```

Shows detailed metadata:

```
Access: (0644/-rw-r--r--)  Uid: (1001/alice)  Gid: (1001/devs)
```

---

## 📦 **9. Default Permissions (umask)**

`umask` defines **default permission mask** for new files/directories.

View current umask:

```bash
$ umask
```

Example output:

```
0022
```

Calculate defaults:

* File = `666 - umask`
* Directory = `777 - umask`

Example:
umask = 022
→ files = 644, dirs = 755

Change temporarily:

```bash
$ umask 002
```

---

## 🧠 **10. Practical Examples**

```bash
$ chmod 755 script.sh
$ chmod g+w data.txt
$ sudo chown root:admins secure.conf
$ chmod u+s /usr/local/bin/customcmd
$ chmod +t /shared/tmpdir
$ stat /etc/passwd
```

---

## 🎯 **Common Interview Questions — Section 9**

1. **Explain the 10-character permission string in `ls -l`.**
   → Type + owner + group + others (e.g., `-rwxr-xr--`)

2. **What’s the numeric value of `rwxr-xr--`?**
   → 754

3. **How to add execute permission only for the owner?**
   → `chmod u+x file`

4. **How to change both user and group ownership?**
   → `chown user:group file`

5. **Difference between `chown` and `chgrp`?**
   → `chown` changes owner/group; `chgrp` changes group only.

6. **What is SUID and where is it used?**
   → Run program as file owner’s privilege (e.g., `/usr/bin/passwd`).

7. **What is the Sticky Bit used for?**
   → Restrict users from deleting others’ files (e.g., `/tmp`).

8. **How to check umask and what does it do?**
   → `umask` defines default file permission creation mask.

9. **What are directory execute permissions used for?**
   → To allow entering (`cd`) the directory.

10. **What does `chmod 4755` mean?**
    → SUID set + owner rwx + group r-x + others r-x.

---

✅ **Recap**
You now understand:

* Permission structure (symbolic & numeric)
* Ownership management
* Special permission bits
* Default umask
* Practical file security handling

---

# 💽 **Section 10: Disk Management and Storage Commands**

---

Linux treats everything as a file, including disks and partitions. Understanding **disk commands** is crucial for monitoring storage, creating partitions, mounting filesystems, and troubleshooting disk issues.

---

## 🧩 **1. Viewing Disk Information**

### **a) `df` — Disk Free Space**

Shows available and used space on mounted filesystems.

```bash
$ df -h
```

Options:

| Option | Meaning                 |
| ------ | ----------------------- |
| `-h`   | Human-readable (GB, MB) |
| `-T`   | Show filesystem type    |

Example output:

```
Filesystem      Type  Size  Used Avail Use% Mounted on
/dev/sda1       ext4   50G   20G   28G  42% /
tmpfs           tmpfs 2G     0    2G   0% /dev/shm
```

---

### **b) `du` — Disk Usage**

Shows **size of directories/files**.

```bash
$ du -sh /var/log
```

Options:

| Option | Meaning              |
| ------ | -------------------- |
| `-s`   | Summary (total only) |
| `-h`   | Human-readable       |
| `-a`   | Include all files    |

---

### **c) `lsblk` — List Block Devices**

Displays **disks, partitions, and mount points**.

```bash
$ lsblk
```

Example output:

```
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0   100G  0 disk
├─sda1   8:1    0    50G  0 part /
├─sda2   8:2    0    30G  0 part /home
└─sda3   8:3    0    20G  0 part /data
```

---

### **d) `fdisk` — Partition Table Manipulation**

Interactive tool to **create, delete, or view partitions**.

```bash
$ sudo fdisk -l
```

> Lists partitions and disk information.

To modify a disk:

```bash
$ sudo fdisk /dev/sda
```

Inside fdisk:

* `n` → create new partition
* `d` → delete partition
* `p` → print partition table
* `w` → write changes to disk

---

### **e) `parted` — Advanced Partitioning**

Better for large disks (>2TB) and GPT:

```bash
$ sudo parted /dev/sda
```

Inside parted:

* `print` → show partitions
* `mklabel gpt` → create GPT table
* `mkpart primary ext4 0% 50G` → create partition

---

## 🧰 **2. Filesystem Management**

### **a) Creating a Filesystem**

```bash
$ sudo mkfs.ext4 /dev/sda1
```

Other types:

```bash
$ sudo mkfs.xfs /dev/sdb1
$ sudo mkfs.vfat /dev/sdc1
```

---

### **b) Checking Filesystem**

```bash
$ sudo fsck /dev/sda1
```

* `fsck` repairs filesystem errors.
* Always unmount before checking: `sudo umount /dev/sda1`.

---

## 🗂️ **3. Mounting and Unmounting Filesystems**

### **a) Temporary Mount**

```bash
$ sudo mount /dev/sda1 /mnt
```

Check mounts:

```bash
$ mount | grep /dev/sda1
```

### **b) Unmount**

```bash
$ sudo umount /mnt
```

### **c) Mount with Filesystem Type**

```bash
$ sudo mount -t ext4 /dev/sda1 /mnt
```

---

### **d) Permanent Mounts (`/etc/fstab`)**

Add entry in `/etc/fstab` for auto-mount:

```
/dev/sda1   /data   ext4   defaults  0  2
```

Columns:

1. Device
2. Mount point
3. Filesystem
4. Options
5. Dump (backup)
6. FSCK order

Mount all fstab entries:

```bash
$ sudo mount -a
```

---

## 📊 **4. Checking Disk Health**

### **a) SMART Status**

```bash
$ sudo smartctl -a /dev/sda
```

* Needs `smartmontools` package.
* Checks disk health and predicts failures.

### **b) Disk Usage Summary**

```bash
$ sudo du -sh /home/*
```

* Finds largest directories/files.

---

## 🧠 **5. Disk Quota Management**

### **a) Enable Quotas**

```bash
$ sudo mount -o remount,usrquota /home
```

### **b) Check Quotas**

```bash
$ quota -u username
```

### **c) Set Quota**

```bash
$ sudo edquota username
```

---

## 🧩 **6. LVM (Logical Volume Management)**

Linux allows **dynamic storage management** using LVM:

### **a) View LVM**

```bash
$ sudo pvdisplay   # Physical volumes
$ sudo vgdisplay   # Volume groups
$ sudo lvdisplay   # Logical volumes
```

### **b) Create LVM**

```bash
$ sudo lvcreate -n lv_data -L 10G vg01
```

### **c) Extend LVM**

```bash
$ sudo lvextend -L +5G /dev/vg01/lv_data
$ sudo resize2fs /dev/vg01/lv_data
```

---

## 🧩 **7. Swap Management**

### **a) Check Swap**

```bash
$ swapon --show
```

### **b) Create Swap**

```bash
$ sudo fallocate -l 2G /swapfile
$ sudo chmod 600 /swapfile
$ sudo mkswap /swapfile
$ sudo swapon /swapfile
```

### **c) Make Swap Permanent**

Add to `/etc/fstab`:

```
/swapfile  none  swap  sw  0 0
```

---

## 🔧 **8. Useful Disk Commands Summary**

| Command                | Purpose                 |
| ---------------------- | ----------------------- |
| `df -h`                | Disk free space         |
| `du -sh /path`         | Disk usage of directory |
| `lsblk`                | List disks & partitions |
| `fdisk -l`             | View partition table    |
| `mkfs`                 | Format partition        |
| `mount /dev/sdx /mnt`  | Mount filesystem        |
| `umount /mnt`          | Unmount filesystem      |
| `fsck /dev/sdx`        | Check/repair filesystem |
| `smartctl -a /dev/sdx` | Disk health check       |
| `lvcreate/lvextend`    | LVM management          |
| `swapon/swapoff`       | Swap management         |

---

## 🎯 **Common Interview Questions — Section 10**

1. **How to check disk space usage?**
   → `df -h` and `du -sh /path`

2. **Difference between `df` and `du`?**
   → `df` shows filesystem usage, `du` shows directory/file usage.

3. **How to list partitions and their mount points?**
   → `lsblk`

4. **How to create a new partition?**
   → `fdisk /dev/sdx` or `parted /dev/sdx`

5. **How to create and mount a filesystem?**
   → `mkfs.ext4 /dev/sdx1` then `mount /dev/sdx1 /mnt`

6. **What is `/etc/fstab` used for?**
   → To configure automatic mounting of filesystems at boot.

7. **How to check disk health?**
   → `sudo smartctl -a /dev/sdx`

8. **How to extend LVM logical volume?**
   → `lvextend -L +Size /dev/vg/lv` then `resize2fs /dev/vg/lv`

9. **How to create swap file and enable it?**
   → `fallocate -l 2G /swapfile; mkswap; swapon`

10. **Difference between physical disk partitioning and LVM?**
    → LVM allows dynamic resizing, snapshots, and pooling storage; physical partitions are static.

---

# 🛠️ **Section 11: Process Management in Linux**

---

In Linux, everything runs as a **process**. A process is essentially a program in execution, and managing them efficiently is key for performance, debugging, and automation.

---

## 🧩 **1. Understanding Processes**

Each process has:

* **PID (Process ID)** – unique number
* **PPID (Parent Process ID)** – process that spawned it
* **UID / GID** – owner
* **State** – running, sleeping, stopped, zombie
* **CPU & memory usage**

### Common process states:

| State | Meaning                                      |
| ----- | -------------------------------------------- |
| R     | Running / runnable                           |
| S     | Sleeping (interruptible)                     |
| D     | Uninterruptible sleep (disk wait)            |
| T     | Stopped (signal)                             |
| Z     | Zombie (terminated but parent not read exit) |

---

## 🧰 **2. Viewing Processes**

### **a) `ps` — Snapshot of Processes**

```bash
$ ps aux
```

* `a` → all users
* `u` → display user/owner
* `x` → show processes without terminal

Columns:

* USER, PID, %CPU, %MEM, VSZ, RSS, STAT, START, TIME, COMMAND

Example:

```
root      1010  0.0  1.2 250000 12300 ?   Ss   10:10  0:01 sshd
```

---

### **b) `top` — Interactive Process Monitor**

```bash
$ top
```

Shows:

* CPU / memory usage
* Running processes sorted by CPU usage
* Process IDs (PIDs), states, and resource usage

Useful keys inside `top`:

* `M` → sort by memory
* `P` → sort by CPU
* `k` → kill a process by PID
* `q` → quit

---

### **c) `htop` — Enhanced `top`**

```bash
$ htop
```

* Colorful, interactive
* Navigate with arrows
* Kill processes without typing PID

> Install if missing:

```bash
$ sudo apt install htop   # Debian/Ubuntu
$ sudo yum install htop   # RHEL/CentOS
```

---

### **d) `pidof` and `pgrep`**

Find PID by process name:

```bash
$ pidof nginx
$ pgrep -l ssh
```

---

## 🔧 **3. Controlling Processes**

### **a) `kill` — Terminate Process**

```bash
$ kill PID
```

* Sends `SIGTERM` by default (graceful exit)

Other signals:

* `-9` → `SIGKILL` (force kill)
* `-15` → `SIGTERM` (default, graceful)

Example:

```bash
$ kill -9 1234
```

---

### **b) `killall` — Kill by Name**

```bash
$ killall firefox
```

* Kills all processes with that name

---

### **c) Background and Foreground Jobs**

#### Run command in background:

```bash
$ sleep 100 &
```

* `&` → send process to background

Check jobs:

```bash
$ jobs
```

Bring job to foreground:

```bash
$ fg %1
```

Send foreground job to background:

```bash
$ Ctrl+Z   # Stop the job
$ bg %1    # Resume in background
```

---

### **d) `nice` and `renice` — Process Priority**

Linux allows **CPU scheduling priority** for processes.

* Priority range: `-20` (highest) → `19` (lowest)

Start process with nice:

```bash
$ nice -n 10 myscript.sh
```

Change running process priority:

```bash
$ renice -n 5 -p 1234
```

---

### **e) `uptime` and Load Average**

Check system load:

```bash
$ uptime
```

Output:

```
10:30:01 up 10 days, 3:15, 2 users, load average: 0.12, 0.34, 0.25
```

* Load average: 1, 5, 15 minutes

---

## 📊 **4. Monitoring Resource Usage**

### **a) Memory Usage**

```bash
$ free -h
```

### **b) Per-process resource**

```bash
$ ps aux --sort=-%mem | head -n 10
$ ps aux --sort=-%cpu | head -n 10
```

### **c) Real-time I/O**

```bash
$ iotop
```

---

### **e) Process Tree**

View parent-child relationships:

```bash
$ pstree
```

---

## 🔧 **5. Advanced Process Management**

* **Zombie processes**: Terminated processes waiting for parent

  ```bash
  $ ps aux | grep Z
  ```
* **Orphan processes**: Parent died, adopted by `init` (PID 1)
* **Daemon processes**: Background services (sshd, nginx)

---

## 🎯 **Common Interview Questions — Section 11**

1. **Difference between `ps` and `top`?**
   → `ps` is a snapshot, `top` is real-time.

2. **How to kill a process by PID and by name?**
   → `kill PID`, `killall process_name`

3. **What is a zombie process?**
   → Process terminated but parent hasn’t read its exit code.

4. **How to run a process in background?**
   → Append `&` or use `bg` after `Ctrl+Z`.

5. **What is `nice` and `renice`?**
   → Set CPU scheduling priority for processes.

6. **How to find processes consuming most memory or CPU?**
   → `ps aux --sort=-%mem` or `top`

7. **Difference between foreground and background process?**
   → Foreground interacts with terminal; background runs without blocking terminal.

8. **How to bring a background job to foreground?**
   → `fg %job_number`

9. **Explain load average in `uptime`.**
   → Average number of processes waiting to run in last 1, 5, 15 mins.

10. **How to view process tree?**
    → `pstree`

---

# 🌐 **Section 12: Networking Commands in Linux**

---

Networking is crucial for connecting systems, diagnosing issues, and managing servers. Linux provides a wide array of commands to monitor, configure, and troubleshoot networks.

---

## 🧩 **1. Viewing Network Interfaces**

### **a) `ip` — Modern Replacement for ifconfig**

```bash
$ ip addr show
```

or shorthand:

```bash
$ ip a
```

* Displays interfaces, IP addresses, and status.
* Example:

```
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet 192.168.1.10/24 brd 192.168.1.255 scope global dynamic enp0s3
```

Other useful `ip` commands:

```bash
$ ip link show          # Show interface status
$ ip route show         # Show routing table
$ ip -s link            # Show statistics
```

---

### **b) `ifconfig` — Legacy Tool**

```bash
$ ifconfig
```

* Shows interface IPs, netmask, and status.
* Install on modern systems:

```bash
$ sudo apt install net-tools
```

---

## 🧰 **2. Checking Connectivity**

### **a) `ping`**

Test connectivity to a host:

```bash
$ ping google.com
```

* Ctrl+C to stop
* `ping -c 4 google.com` → send 4 packets

### **b) `traceroute`**

Shows the path packets take to reach a host:

```bash
$ traceroute google.com
```

* On some systems: `sudo apt install traceroute`

### **c) `mtr` — Real-time traceroute + ping**

```bash
$ mtr google.com
```

---

## 🧩 **3. DNS Lookup Commands**

### **a) `nslookup`**

```bash
$ nslookup google.com
```

* Returns IP addresses for a domain

### **b) `dig`**

```bash
$ dig google.com
```

* More detailed DNS info
* Query specific record type:

```bash
$ dig A google.com
$ dig MX google.com
```

---

## 🧰 **4. Network Connections & Listening Ports**

### **a) `netstat` — Legacy Tool**

```bash
$ netstat -tuln
```

* `-t` → TCP
* `-u` → UDP
* `-l` → Listening
* `-n` → Show numeric ports/IPs

### **b) `ss` — Modern Replacement**

```bash
$ ss -tuln
```

* Shows listening sockets
* `ss -p` → Show process using socket

### **c) `lsof` — List Open Files**

```bash
$ sudo lsof -i :80
```

* Shows which process is using port 80

---

## 🔧 **5. File Transfer & Download**

### **a) `curl`**

```bash
$ curl -O http://example.com/file.txt
```

* `-O` → Save with original filename
* Test API:

```bash
$ curl -I http://example.com
```

### **b) `wget`**

```bash
$ wget http://example.com/file.txt
```

* Recursive download:

```bash
$ wget -r http://example.com
```

---

## 🧩 **6. Routing & Network Configuration**

### **a) `route` / `ip route`**

View default gateway:

```bash
$ ip route show
```

Example:

```
default via 192.168.1.1 dev enp0s3
192.168.1.0/24 dev enp0s3 proto kernel scope link src 192.168.1.10
```

### **b) Add/Delete Routes**

```bash
$ sudo ip route add 10.0.0.0/24 via 192.168.1.1
$ sudo ip route del 10.0.0.0/24
```

---

## 🧰 **7. Firewall Management**

### **a) `ufw` — Simple Firewall (Ubuntu/Debian)**

```bash
$ sudo ufw status
$ sudo ufw enable
$ sudo ufw allow 22/tcp
$ sudo ufw deny 80/tcp
```

### **b) `firewalld` — RHEL/CentOS**

```bash
$ sudo firewall-cmd --state
$ sudo firewall-cmd --permanent --add-service=http
$ sudo firewall-cmd --reload
```

---

## 🧩 **8. Network Performance Testing**

### **a) Bandwidth Test with `iperf3`**

```bash
$ iperf3 -s   # On server
$ iperf3 -c server_ip  # On client
```

### **b) Real-time Traffic Monitoring**

```bash
$ iftop
$ nload
```

---

## 📊 **9. Useful Networking Commands Summary**

| Command         | Purpose                        |
| --------------- | ------------------------------ |
| `ip addr`       | Show IP addresses & interfaces |
| `ping`          | Test connectivity              |
| `traceroute`    | Show path to host              |
| `nslookup`      | DNS query                      |
| `dig`           | Advanced DNS query             |
| `netstat -tuln` | View listening ports           |
| `ss -tuln`      | Modern alternative for netstat |
| `lsof -i :port` | Process using port             |
| `curl`          | Download files / test HTTP     |
| `wget`          | Download files                 |
| `ip route`      | View routing table             |
| `ufw/firewalld` | Firewall management            |
| `iperf3`        | Bandwidth test                 |
| `iftop/nload`   | Real-time traffic              |

---

## 🎯 **Common Interview Questions — Section 12**

1. **How to check your server’s IP address?**
   → `ip addr` or `ifconfig`

2. **How to check connectivity to a remote host?**
   → `ping hostname/ip`

3. **Difference between `netstat` and `ss`?**
   → `ss` is faster, modern replacement for `netstat`.

4. **How to find which process is using a port?**
   → `lsof -i :port` or `ss -tulpn`

5. **How to check DNS records?**
   → `nslookup domain` or `dig domain`

6. **How to check the route to a remote host?**
   → `traceroute hostname` or `ip route get hostname`

7. **Difference between `curl` and `wget`?**
   → `curl` mainly for APIs and flexible requests; `wget` for downloading files recursively.

8. **How to view listening TCP/UDP ports?**
   → `ss -tuln` or `netstat -tuln`

9. **How to temporarily allow HTTP traffic in firewall?**
   → `sudo ufw allow 80/tcp` or `firewall-cmd --add-service=http --permanent`

10. **How to test network bandwidth between two hosts?**
    → `iperf3 -s` (server) and `iperf3 -c server_ip` (client)

---

# 📦 **Section 13: Package Management in Linux**

---

Linux distributions have different package management systems depending on whether they are **Debian-based** or **RHEL-based**. Understanding both is crucial for administration and troubleshooting.

---

## 🧩 **1. Debian/Ubuntu Systems – `apt`**

### **a) Update Package Lists**

```bash
$ sudo apt update
```

* Fetch latest package information from repositories.

### **b) Upgrade Installed Packages**

```bash
$ sudo apt upgrade
```

* Upgrades all installed packages to latest version.

### **c) Install Packages**

```bash
$ sudo apt install package_name
```

* Example: `sudo apt install vim`

### **d) Remove Packages**

```bash
$ sudo apt remove package_name
$ sudo apt purge package_name   # Remove config files as well
```

### **e) Search Packages**

```bash
$ apt search package_name
```

### **f) Show Package Details**

```bash
$ apt show package_name
```

---

## 🧰 **2. RHEL/CentOS/Fedora Systems – `yum` and `dnf`**

### **a) `yum` – Older RHEL/CentOS**

```bash
$ sudo yum update
$ sudo yum install package_name
$ sudo yum remove package_name
$ yum list installed
$ yum search package_name
```

### **b) `dnf` – Fedora / New RHEL**

```bash
$ sudo dnf update
$ sudo dnf install package_name
$ sudo dnf remove package_name
$ dnf list installed
$ dnf search package_name
```

> `dnf` is faster and handles dependencies better than `yum`.

---

## 🧩 **3. RPM – Low-Level Package Manager**

* Works on RHEL/CentOS/Fedora.
* Install RPM packages directly:

```bash
$ sudo rpm -ivh package.rpm
```

* Remove RPM packages:

```bash
$ sudo rpm -e package_name
```

* Query packages:

```bash
$ rpm -qa           # List all installed
$ rpm -qi package_name  # Package info
```

---

## 🧰 **4. Universal Linux Package Managers**

### **a) Snap Packages**

* Works across multiple distros.

```bash
$ sudo snap install package_name
$ sudo snap remove package_name
$ snap list            # List installed snaps
```

### **b) Flatpak Packages**

* Alternative universal package system.

```bash
$ flatpak install flathub package_name
$ flatpak remove package_name
$ flatpak list
```

---

## 🧩 **5. Working with Repositories**

### **a) Debian/Ubuntu**

* Add repository:

```bash
$ sudo add-apt-repository ppa:repository_name
$ sudo apt update
```

### **b) RHEL/CentOS/Fedora**

* Enable repository:

```bash
$ sudo yum-config-manager --add-repo repository_url
$ sudo yum repolist
```

---

## 🧰 **6. Package Management Tips**

* Always **update package lists** before installing new software.
* Use **`purge`** in Debian/Ubuntu to remove old configs.
* Check **dependencies** before removing critical packages.
* Prefer **`dnf` or `apt`** over manually downloading RPM/DEB files unless necessary.

---

## 🎯 **Common Interview Questions — Section 13**

1. **Difference between `apt` and `yum`/`dnf`?**
   → `apt` for Debian-based, `yum/dnf` for RHEL-based systems.

2. **How to install a package in Ubuntu?**
   → `sudo apt install package_name`

3. **How to remove a package and its config files?**
   → `sudo apt purge package_name`

4. **Difference between `rpm` and `yum`/`dnf`?**
   → `rpm` manages individual package files, `yum/dnf` handles dependencies and repositories.

5. **How to update all packages on a system?**
   → Debian: `sudo apt update && sudo apt upgrade`
   → RHEL/Fedora: `sudo dnf update`

6. **How to search for a package?**
   → `apt search package_name` or `dnf search package_name`

7. **What is Snap and Flatpak?**
   → Universal package managers across Linux distros.

8. **How to list installed packages?**
   → Debian: `apt list --installed`
   → RHEL: `dnf list installed` or `rpm -qa`

9. **How to add a new repository?**
   → Ubuntu: `add-apt-repository ppa:repo_name`
   → RHEL: `yum-config-manager --add-repo repo_url`

10. **Why use `dnf`/`apt` instead of manually installing `.rpm` or `.deb`?**
    → They handle dependencies automatically and reduce system conflicts.

---

# 💾 **Section 14: Disk Management & Filesystems in Linux**

---

Linux stores data on **filesystems** that reside on **partitions** of disks. Managing disks efficiently is key for performance, data safety, and system administration.

---

## 🧩 **1. Viewing Disk Information**

### **a) `lsblk` — List Block Devices**

```bash
$ lsblk
```

* Shows disks, partitions, sizes, and mount points.
* Example output:

```
NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda      8:0    0  100G  0 disk 
├─sda1   8:1    0   50G  0 part /
├─sda2   8:2    0   49G  0 part /home
└─sda3   8:3    0    1G  0 part [SWAP]
```

### **b) `fdisk` — Partition Table**

```bash
$ sudo fdisk -l
```

* Lists all disks, partitions, and filesystem types.

### **c) `df` — Disk Free Space**

```bash
$ df -h
```

* `-h` → human-readable
* Example:

```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   28G  42% /
```

### **d) `du` — Disk Usage**

```bash
$ du -sh /home/user
```

* `-s` → summary
* `-h` → human-readable

---

## 🧰 **2. Filesystems**

Linux supports multiple filesystems:

| Filesystem | Notes                      |
| ---------- | -------------------------- |
| ext4       | Most common, journaling    |
| xfs        | High-performance, scalable |
| btrfs      | Snapshots, modern features |
| vfat/fat32 | Compatible with Windows    |
| ntfs       | Windows-compatible         |
| swap       | Swap partition for memory  |

### **a) Check Filesystem Type**

```bash
$ df -T
$ lsblk -f
```

### **b) Create a Filesystem**

```bash
$ sudo mkfs.ext4 /dev/sdb1
```

* Replace `ext4` with your desired filesystem.

---

## 🧩 **3. Mounting & Unmounting**

### **a) Mount a Partition**

```bash
$ sudo mount /dev/sdb1 /mnt
```

* `/mnt` → mount point (directory where partition is accessible)

### **b) Unmount a Partition**

```bash
$ sudo umount /mnt
```

### **c) Add Permanent Mount in `/etc/fstab`**

Edit `/etc/fstab` to auto-mount partitions on boot:

```
/dev/sdb1   /data   ext4   defaults   0 2
```

* Format: `<device> <mount_point> <fs_type> <options> <dump> <pass>`

---

## 🧰 **4. Swap Management**

Swap acts as virtual memory.

* Check swap:

```bash
$ swapon --show
$ free -h
```

* Add swap file:

```bash
$ sudo fallocate -l 2G /swapfile
$ sudo chmod 600 /swapfile
$ sudo mkswap /swapfile
$ sudo swapon /swapfile
```

* Make it permanent: add to `/etc/fstab`:

```
/swapfile none swap sw 0 0
```

---

## 🧩 **5. Disk & Filesystem Health**

### **a) Check Disk Usage**

```bash
$ df -h
$ du -sh /path/to/directory
```

### **b) Filesystem Check**

```bash
$ sudo fsck /dev/sdb1
```

* Use when filesystem might be corrupted (unmount first).

### **c) SMART Monitoring**

```bash
$ sudo smartctl -a /dev/sda
```

* Requires `smartmontools`
* Checks disk health and predicts failures.

---

## 🧰 **6. LVM (Logical Volume Management)**

LVM allows dynamic resizing of volumes:

### **a) Basic LVM Commands**

```bash
$ sudo pvcreate /dev/sdb1       # Create physical volume
$ sudo vgcreate vg_data /dev/sdb1  # Create volume group
$ sudo lvcreate -L 10G -n lv_data vg_data  # Create logical volume
$ sudo mkfs.ext4 /dev/vg_data/lv_data      # Format LV
$ sudo mount /dev/vg_data/lv_data /data   # Mount
```

### **b) Resize Logical Volume**

```bash
$ sudo lvextend -L +5G /dev/vg_data/lv_data
$ sudo resize2fs /dev/vg_data/lv_data
```

---

## 🎯 **Common Interview Questions — Section 14**

1. **How to check disk usage on Linux?**
   → `df -h` for overall, `du -sh` for directories.

2. **Difference between `df` and `du`?**
   → `df` shows disk usage of filesystems; `du` shows usage of directories/files.

3. **How to list all partitions?**
   → `lsblk` or `fdisk -l`

4. **How to mount a partition?**
   → `mount /dev/sdb1 /mnt`

5. **How to make a mount permanent?**
   → Edit `/etc/fstab`

6. **How to create a filesystem on a disk?**
   → `mkfs.ext4 /dev/sdb1` (replace `ext4` if needed)

7. **How to check swap space?**
   → `swapon --show` or `free -h`

8. **How to add swap file?**
   → `fallocate`, `chmod`, `mkswap`, `swapon`, add to `/etc/fstab`

9. **What is LVM?**
   → Logical Volume Manager, allows flexible disk partitioning and resizing.

10. **How to check disk health?**
    → `smartctl -a /dev/sda` or `fsck /dev/sda1`

---

# ⏰ **Section 15: Cron Jobs & Task Scheduling**

---

Linux allows you to **schedule commands or scripts** to run automatically at specified times using `cron` and `at`.

---

## 🧩 **1. Cron Jobs**

`cron` is a daemon that executes scheduled tasks repeatedly.

### **a) Crontab Syntax**

```
* * * * * command_to_run
| | | | |
| | | | ----- Day of week (0-7) (Sunday=0 or 7)
| | | ------- Month (1-12)
| | --------- Day of month (1-31)
| ----------- Hour (0-23)
------------- Minute (0-59)
```

### **b) Common Time Examples**

| Time Spec      | Meaning                        |
| -------------- | ------------------------------ |
| `0 5 * * *`    | Every day at 5:00 AM           |
| `*/10 * * * *` | Every 10 minutes               |
| `0 0 1 * *`    | 1st of every month at midnight |

---

### **c) Editing Crontab**

* Edit current user’s crontab:

```bash
$ crontab -e
```

* List crontab jobs:

```bash
$ crontab -l
```

* Remove crontab jobs:

```bash
$ crontab -r
```

---

### **d) Example Cron Jobs**

1. Backup `/home/user` every day at 2 AM:

```bash
0 2 * * * tar -czf /backup/home_$(date +\%F).tar.gz /home/user
```

2. Run a script every 15 minutes:

```bash
*/15 * * * * /home/user/scripts/myscript.sh
```

---

## 🧰 **2. Cron Directories**

System-wide cron jobs can also be placed in:

| Directory            | Description                                 |
| -------------------- | ------------------------------------------- |
| `/etc/crontab`       | System-wide cron with an extra “user” field |
| `/etc/cron.hourly/`  | Scripts run hourly                          |
| `/etc/cron.daily/`   | Scripts run daily                           |
| `/etc/cron.weekly/`  | Scripts run weekly                          |
| `/etc/cron.monthly/` | Scripts run monthly                         |

> Scripts in these directories are executed automatically by the system.

---

## 🧩 **3. `at` — One-time Scheduling**

`at` schedules a **single task** at a specified time.

### **a) Install `at` (if needed)**

```bash
$ sudo apt install at        # Debian/Ubuntu
$ sudo yum install at        # RHEL/CentOS
```

### **b) Schedule a Task**

```bash
$ echo "sh /home/user/myscript.sh" | at 14:30
```

* Runs at 2:30 PM today.

### **c) List Scheduled Tasks**

```bash
$ atq
```

### **d) Remove Scheduled Tasks**

```bash
$ atrm job_number
```

---

## 🧰 **4. Managing Cron Logs**

* Cron job output is sent via email to the user (if configured).
* On most systems, logs are in:

```bash
/var/log/cron       # RHEL/CentOS
/var/log/syslog     # Debian/Ubuntu
```

* Example to check cron logs:

```bash
$ grep CRON /var/log/syslog
```

---

## 🧩 **5. Environment Considerations**

* Cron jobs run in a limited environment. Always use **absolute paths**:

```bash
/usr/bin/python3 /home/user/script.py
```

* Set environment variables in the crontab:

```bash
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
```

---

## 🎯 **Common Interview Questions — Section 15**

1. **What is `cron` in Linux?**
   → Daemon that runs scheduled repetitive tasks.

2. **Difference between `cron` and `at`?**
   → `cron` is repetitive, `at` is one-time.

3. **How to edit a user’s crontab?**
   → `crontab -e`

4. **How to list scheduled cron jobs?**
   → `crontab -l`

5. **How to remove all cron jobs for a user?**
   → `crontab -r`

6. **Where are system cron jobs stored?**
   → `/etc/crontab`, `/etc/cron.hourly/`, `/etc/cron.daily/`, etc.

7. **How to schedule a job for every 5 minutes?**
   → `*/5 * * * * command`

8. **Why use absolute paths in cron jobs?**
   → Cron runs with minimal environment; relative paths may fail.

9. **How to schedule a task with `at`?**
   → `echo "command" | at HH:MM`

10. **How to check cron job execution logs?**
    → `grep CRON /var/log/syslog` or `/var/log/cron` depending on distro.

---

# 🖋️ **Section 16: Shell Scripting Basics**

---

A **shell script** is a text file containing a sequence of Linux commands that the shell executes. Shell scripting automates repetitive tasks, simplifies administration, and is widely used in DevOps and system administration.

---

## 🧩 **1. Creating a Shell Script**

### **a) Basic Script**

```bash
#!/bin/bash
# My first script
echo "Hello, Linux!"
```

* `#!/bin/bash` → Shebang, tells the system to use Bash to execute the script.
* Save the file with `.sh` extension (optional but recommended).
* Make the script executable:

```bash
chmod +x script.sh
```

* Run the script:

```bash
./script.sh
```

---

## 🧰 **2. Variables**

* Define variables without spaces:

```bash
name="Alice"
echo "Hello $name"
```

* Read input from user:

```bash
read -p "Enter your name: " name
echo "Hello $name"
```

* Environment variables:

```bash
echo $HOME
echo $PATH
```

---

## 🧩 **3. Conditional Statements**

### **a) If-Else**

```bash
#!/bin/bash
read -p "Enter a number: " num
if [ $num -gt 10 ]; then
    echo "Number is greater than 10"
else
    echo "Number is 10 or less"
fi
```

### **b) Nested If**

```bash
if [ $num -gt 0 ]; then
    echo "Positive"
elif [ $num -lt 0 ]; then
    echo "Negative"
else
    echo "Zero"
fi
```

---

## 🧰 **4. Loops**

### **a) For Loop**

```bash
for i in 1 2 3 4 5
do
    echo "Number: $i"
done
```

### **b) While Loop**

```bash
count=1
while [ $count -le 5 ]
do
    echo "Count: $count"
    ((count++))
done
```

### **c) Until Loop**

```bash
count=1
until [ $count -gt 5 ]
do
    echo "Count: $count"
    ((count++))
done
```

---

## 🧩 **5. Functions**

* Functions help modularize scripts.

```bash
#!/bin/bash
greet() {
    echo "Hello $1"
}
greet "Alice"
```

* `$1` → first argument passed to the function.

---

## 🧰 **6. Command-line Arguments**

* `$0` → script name
* `$1, $2 ...` → positional arguments
* `$#` → number of arguments
* `$@` → all arguments

Example:

```bash
#!/bin/bash
echo "Script Name: $0"
echo "First Arg: $1"
echo "Total Args: $#"
```

---

## 🧩 **7. Error Handling & Exit Status**

* Every command returns an **exit status** (`0` = success, non-zero = error)

```bash
mkdir /tmp/mydir
if [ $? -eq 0 ]; then
    echo "Directory created"
else
    echo "Failed to create directory"
fi
```

* Use `exit` to terminate scripts:

```bash
if [ ! -d /tmp/mydir ]; then
    echo "Directory missing"
    exit 1
fi
```

---

## 🧰 **8. File Operations in Scripts**

```bash
#!/bin/bash
# Check if file exists
if [ -f "/tmp/test.txt" ]; then
    echo "File exists"
else
    echo "File not found"
fi

# Read file line by line
while IFS= read -r line
do
  echo "$line"
done < "/tmp/test.txt"
```

---

## 🎯 **Common Interview Questions — Section 16**

1. **What is a shell script?**
   → A text file with Linux commands executed by the shell.

2. **How do you make a script executable?**
   → `chmod +x script.sh`

3. **What is a shebang (`#!`)?**
   → Specifies the interpreter for the script.

4. **How to read input from user?**
   → `read -p "Prompt" variable`

5. **How to pass arguments to a script?**
   → `$1, $2, ...` positional parameters

6. **How to check if a file exists in a script?**
   → `[ -f "/path/to/file" ]`

7. **Difference between `for`, `while`, and `until` loops?**
   → `for` = fixed iterations, `while` = until condition false, `until` = until condition true

8. **How to define a function in Bash?**
   → `function_name() { commands }`

9. **What is exit status `$?`?**
   → Returns the last command’s success (0) or failure (non-zero)

10. **How to terminate a script with error?**
    → `exit 1` or any non-zero value

---

# 📊 **Section 17: System Monitoring & Performance Tuning**

---

Linux provides a rich set of tools to **monitor system performance** and **optimize resources**. This section covers CPU, memory, disk, and network monitoring.

---

## 🧩 **1. CPU & Process Monitoring**

### **a) `top` — Real-time Process Monitoring**

```bash
$ top
```

* Displays CPU, memory usage, and running processes.

* Key columns:

  * `%CPU` → CPU usage per process
  * `%MEM` → Memory usage
  * `PR` → Priority
  * `NI` → Nice value

* Interactive shortcuts in `top`:

  * `P` → Sort by CPU
  * `M` → Sort by memory
  * `k` → Kill a process
  * `q` → Quit

---

### **b) `htop` — Enhanced `top`**

```bash
$ htop
```

* Requires installation: `sudo apt install htop`
* Provides a **graphical view**, color-coded CPU/memory bars, easy process management.

---

### **c) `ps` — Snapshot of Processes**

```bash
$ ps aux
```

* `a` → all users, `u` → user-friendly format, `x` → include processes without terminal
* Example:

```
USER       PID %CPU %MEM COMMAND
root         1  0.0  0.1 /sbin/init
```

---

## 🧰 **2. Memory Monitoring**

### **a) `free` — Memory Usage**

```bash
$ free -h
```

* `-h` → human-readable
* Columns:

  * `total`, `used`, `free`, `shared`, `buffers/cache`, `available`

### **b) `/proc/meminfo`**

```bash
$ cat /proc/meminfo
```

* Provides detailed memory statistics.

---

## 🧩 **3. Disk I/O & Storage Monitoring**

### **a) `df` — Disk Usage**

```bash
$ df -h
```

* Shows total, used, and available disk space.

### **b) `du` — Directory/File Usage**

```bash
$ du -sh /var/log
```

### **c) `iostat` — Disk I/O**

```bash
$ iostat -x 2
```

* `-x` → extended statistics
* `2` → refresh every 2 seconds
* Monitors read/write speeds, IOPS, utilization.

### **d) `iotop` — Real-time I/O**

```bash
$ sudo iotop
```

* Requires installation
* Shows disk I/O usage per process in real-time.

---

## 🧰 **4. Network Monitoring**

### **a) `ifconfig` / `ip`**

```bash
$ ifconfig
$ ip addr show
```

* Displays network interfaces, IP addresses, and status.

### **b) `netstat` / `ss`**

```bash
$ netstat -tulnp
$ ss -tulnp
```

* Lists active TCP/UDP connections and listening ports.

### **c) `ping` & `traceroute`**

```bash
$ ping google.com
$ traceroute google.com
```

* Check connectivity and network path.

### **d) `nload`**

```bash
$ nload
```

* Real-time incoming/outgoing traffic per interface (requires installation).

---

## 🧩 **5. System Logs Monitoring**

* System logs help troubleshoot performance issues:

```bash
$ tail -f /var/log/syslog       # Debian/Ubuntu
$ tail -f /var/log/messages     # RHEL/CentOS
$ journalctl -xe
```

* Monitor logs in real-time to catch errors or performance bottlenecks.

---

## 🧰 **6. Performance Optimization Tips**

1. **CPU**

   * Kill unnecessary processes: `kill PID` or `killall process_name`
   * Adjust process priority: `nice`, `renice`

2. **Memory**

   * Monitor memory leaks using `top` or `ps`
   * Add swap if needed: `fallocate`, `swapon`

3. **Disk**

   * Clean logs: `logrotate`, `rm /var/log/*.log`
   * Monitor slow I/O with `iostat` and `iotop`

4. **Network**

   * Check for network saturation using `nload`, `iftop`
   * Adjust firewall or throttling if needed

---

## 🎯 **Common Interview Questions — Section 17**

1. **How to check CPU usage in Linux?**
   → `top`, `htop`, `mpstat`

2. **Difference between `top` and `htop`?**
   → `htop` is interactive, color-coded, easier to manage.

3. **How to monitor memory usage?**
   → `free -h`, `/proc/meminfo`, `top`

4. **How to check disk space usage?**
   → `df -h` for partitions, `du -sh` for directories

5. **How to monitor disk I/O?**
   → `iostat`, `iotop`

6. **How to list active network connections?**
   → `netstat -tulnp` or `ss -tulnp`

7. **How to check network traffic in real-time?**
   → `nload`, `iftop`

8. **Where are Linux system logs stored?**
   → `/var/log/syslog`, `/var/log/messages`, `journalctl`

9. **How to kill a process consuming high CPU?**
   → `kill PID` or `killall process_name`

10. **How to adjust process priority?**
    → `nice -n 10 command`, `renice -n 5 PID`

---

# 🐳 **Section 18: Docker & Containers Basics**

---

Docker is a **containerization platform** that allows you to package applications with all dependencies into a **portable container**, ensuring consistency across environments.

---

## 🧩 **1. Key Docker Concepts**

1. **Image** – Read-only template used to create containers (like a snapshot of OS + app).
2. **Container** – Running instance of an image.
3. **Docker Daemon** – Background service managing containers (`dockerd`).
4. **Docker CLI** – Command-line interface to interact with Docker (`docker`).
5. **Dockerfile** – Script defining how to build an image.
6. **Registry** – Storage for Docker images (e.g., Docker Hub).

---

## 🧰 **2. Installing Docker (Linux)**

### On Ubuntu:

```bash
sudo apt update
sudo apt install docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker $USER   # allow non-root usage
```

### Check installation:

```bash
docker --version
docker info
```

---

## 🧩 **3. Basic Docker Commands**

### **a) Images**

```bash
docker pull ubuntu          # download image
docker images               # list local images
docker rmi ubuntu           # remove image
```

### **b) Containers**

```bash
docker run -it ubuntu /bin/bash    # start container interactively
docker ps                          # list running containers
docker ps -a                       # list all containers
docker stop <container_id>         # stop container
docker start <container_id>        # start container
docker rm <container_id>           # remove container
```

### **c) Logs & Stats**

```bash
docker logs <container_id>
docker stats                        # live container resource usage
```

---

## 🧰 **4. Managing Docker Images**

* **Build image from Dockerfile**

```bash
docker build -t myapp:1.0 .
```

* **Push to Docker Hub**

```bash
docker login
docker tag myapp:1.0 username/myapp:1.0
docker push username/myapp:1.0
```

---

## 🧩 **5. Docker Volumes**

* Persist data outside containers.

```bash
docker volume create myvol
docker run -v myvol:/data ubuntu /bin/bash
```

* List volumes:

```bash
docker volume ls
```

* Remove volume:

```bash
docker volume rm myvol
```

---

## 🧰 **6. Docker Networks**

* **Bridge network** (default) → containers can talk to each other.

```bash
docker network ls
docker network create mynet
docker run --network mynet --name app1 ubuntu
docker run --network mynet --name app2 ubuntu
```

* **Inspect network**

```bash
docker network inspect mynet
```

---

## 🧩 **7. Dockerfile Basics**

Example `Dockerfile`:

```dockerfile
# Base image
FROM ubuntu:22.04

# Maintainer
LABEL maintainer="alice@example.com"

# Install packages
RUN apt update && apt install -y python3

# Copy application code
COPY app.py /app/app.py

# Set working directory
WORKDIR /app

# Run app
CMD ["python3", "app.py"]
```

* Build and run:

```bash
docker build -t mypythonapp .
docker run -it mypythonapp
```

---

## 🧰 **8. Docker Compose (Optional)**

* For multi-container apps using `docker-compose.yml`.

```yaml
version: '3'
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  db:
    image: mysql
    environment:
      MYSQL_ROOT_PASSWORD: root
```

* Commands:

```bash
docker-compose up
docker-compose down
docker-compose logs
```

---

## 🎯 **Common Docker Interview Questions**

1. **What is Docker?**
   → Containerization platform to run applications in isolated environments.

2. **Difference between Docker Image and Container?**
   → Image = template, Container = running instance.

3. **How to list all running containers?**
   → `docker ps`

4. **How to remove a container?**
   → `docker rm <container_id>`

5. **How to persist data in Docker?**
   → Use **volumes** with `-v` flag.

6. **What is Dockerfile?**
   → Script defining instructions to build an image.

7. **How to expose ports from container to host?**
   → `docker run -p host_port:container_port image_name`

8. **How to connect containers to a custom network?**
   → `docker network create mynet` and `docker run --network mynet`

9. **What is Docker Compose?**
   → Tool to define and run multi-container apps using YAML files.

10. **Difference between Docker and Virtual Machines?**
    → Docker shares host OS kernel, lightweight. VM has separate OS, heavy.

---

# 🖥️ **Section 19: Terminal Multiplexers — Screen & Tmux**

Terminal multiplexers let you **run multiple terminal sessions in one window**, detach, and resume later. This is especially useful for **SSH sessions** and long-running processes.

---

## 🧩 **1. GNU Screen**

**Screen** is an older terminal multiplexer but still widely used.

### **Install Screen**

```bash
sudo apt install screen       # Ubuntu/Debian
sudo yum install screen       # RHEL/CentOS
```

### **Basic Commands**

* Start a new screen session:

```bash
screen -S session_name
```

* Detach from a session (leave it running):

```
Ctrl + a, d
```

* List existing sessions:

```bash
screen -ls
```

* Reattach to a session:

```bash
screen -r session_name
```

* Kill a session:

```bash
screen -X -S session_name quit
```

### **Screen Tips**

* Split windows: `Ctrl+a` then `S`
* Switch between windows: `Ctrl+a` then `n` or `p`
* Scroll inside screen: `Ctrl+a` then `[` (enter copy mode)

---

## 🧰 **2. Tmux (Terminal Multiplexer)**

**Tmux** is newer, more powerful, and highly configurable. Many developers prefer it over screen.

### **Install Tmux**

```bash
sudo apt install tmux       # Ubuntu/Debian
sudo yum install tmux       # RHEL/CentOS
```

### **Basic Commands**

* Start tmux session:

```bash
tmux new -s session_name
```

* Detach session (keep it running):

```
Ctrl + b, d
```

* List sessions:

```bash
tmux ls
```

* Reattach to a session:

```bash
tmux attach -t session_name
```

* Kill session:

```bash
tmux kill-session -t session_name
```

---

### **Tmux Windows & Panes**

* Create new window:

```
Ctrl + b, c
```

* Switch windows:

```
Ctrl + b, n   # next
Ctrl + b, p   # previous
```

* Split panes horizontally:

```
Ctrl + b, "
```

* Split panes vertically:

```
Ctrl + b, %
```

* Navigate panes:

```
Ctrl + b, arrow keys
```

* Resize panes:

```
Ctrl + b, hold Ctrl + arrow keys
```

* Close a pane/window:

```
exit
```

---

### **Tmux Customization**

* Config file: `~/.tmux.conf`
* Example: change prefix key (default is Ctrl+b):

```bash
set -g prefix C-a
unbind C-b
bind C-a send-prefix
```

* Enable mouse support:

```bash
set -g mouse on
```

---

## 🎯 **Common Interview Questions — Screen & Tmux**

1. **What is a terminal multiplexer?**
   → Tool to run multiple terminal sessions in one window, detach, and reattach later.

2. **Difference between `screen` and `tmux`?**
   → Tmux is newer, more customizable, supports panes, easier scripting; screen is older, simpler.

3. **How to detach a tmux session?**
   → `Ctrl+b` then `d`

4. **How to reattach a tmux session?**
   → `tmux attach -t session_name`

5. **How to split a tmux window into panes?**
   → `Ctrl+b` then `%` (vertical) or `"` (horizontal)

6. **How to list all screen sessions?**
   → `screen -ls`

7. **How to kill a screen session?**
   → `screen -X -S session_name quit`

---

# 📝 **Section 20: Ultimate Linux & Docker Interview Q&A**

---

## **1. Linux Basics**

**Q1:** What is Linux?
**A:** Linux is an open-source, Unix-like operating system kernel, used in servers, desktops, and embedded systems.

**Q2:** How to check current user?
**A:** `whoami`

**Q3:** How to list files and directories?
**A:** `ls -l`, `ls -a`

**Q4:** How to change directories?
**A:** `cd /path/to/directory`

**Q5:** Difference between `su` and `sudo`?
**A:** `su` switches user, `sudo` runs commands with elevated privileges without switching.

---

## **2. File & Directory Management**

**Q1:** How to copy, move, and delete files?
**A:** `cp source dest`, `mv source dest`, `rm file`

**Q2:** How to search for files?
**A:** `find /path -name filename`

**Q3:** How to display file content?
**A:** `cat file`, `less file`, `head file`, `tail file`

**Q4:** How to change permissions and ownership?
**A:** `chmod 755 file`, `chown user:group file`

**Q5:** What is `umask`?
**A:** Default permission mask for new files/directories.

---

## **3. Process & Job Management**

**Q1:** How to see running processes?
**A:** `ps aux`, `top`, `htop`

**Q2:** How to kill a process?
**A:** `kill PID` or `kill -9 PID`

**Q3:** How to run a process in the background?
**A:** Append `&` to command: `./script.sh &`

**Q4:** How to view background jobs?
**A:** `jobs`, `fg`, `bg`

---

## **4. Disk & System Monitoring**

**Q1:** How to check disk usage?
**A:** `df -h`

**Q2:** How to check memory usage?
**A:** `free -h`

**Q3:** How to check CPU usage?
**A:** `top`, `htop`, `mpstat`

**Q4:** How to monitor network traffic?
**A:** `ifconfig`, `ip addr`, `netstat -tulnp`, `ss -tulnp`

---

## **5. Networking**

**Q1:** How to check active connections?
**A:** `netstat -tulnp` or `ss -tulnp`

**Q2:** How to ping a server?
**A:** `ping google.com`

**Q3:** How to trace route to a host?
**A:** `traceroute google.com`

**Q4:** How to check open ports?
**A:** `nmap host_ip`

---

## **6. Shell Scripting**

**Q1:** How to declare a variable?
**A:** `name="value"`

**Q2:** How to write a for loop?
**A:**

```bash
for i in {1..5}; do
  echo $i
done
```

**Q3:** How to check exit status?
**A:** `$?`

**Q4:** How to schedule jobs?
**A:** `cron` or `at`

---

## **7. Security & Permissions**

**Q1:** What is SUID, SGID, Sticky bit?
**A:**

* SUID → Run as file owner
* SGID → Run as group owner
* Sticky → Prevent deletion by non-owner in shared directories

**Q2:** How to view ACLs?
**A:** `getfacl file`

**Q3:** How to enable firewall with UFW?
**A:** `sudo ufw enable`, `sudo ufw allow 22/tcp`

**Q4:** How to temporarily disable SELinux?
**A:** `sudo setenforce 0`

---

## **8. Package Management**

**Q1:** Install a package on Ubuntu/Debian?
**A:** `sudo apt install package_name`

**Q2:** Install a package on RHEL/CentOS?
**A:** `sudo yum install package_name`

**Q3:** Update all packages?
**A:** `sudo apt update && sudo apt upgrade`

---

## **9. Docker**

**Q1:** What is Docker?
**A:** Platform for containerizing applications with dependencies.

**Q2:** Difference between image and container?
**A:** Image = template, Container = running instance.

**Q3:** Run a container interactively?
**A:** `docker run -it ubuntu /bin/bash`

**Q4:** Build an image from Dockerfile?
**A:** `docker build -t myapp:1.0 .`

**Q5:** Persist data in Docker?
**A:** Use volumes: `docker run -v myvol:/data ubuntu`

**Q6:** List all running containers?
**A:** `docker ps`

**Q7:** Stop and remove a container?
**A:** `docker stop <id>` → `docker rm <id>`

**Q8:** What is Docker Compose?
**A:** Tool to define and run multi-container applications using a YAML file.

---

## **10. Screen / Tmux**

**Q1:** Difference between screen and tmux?
**A:** Tmux is more modern, supports panes/windows, better scripting; screen is simpler and older.

**Q2:** Detach and reattach a screen session?
**A:** `Ctrl+a, d` → detach, `screen -r` → reattach

**Q3:** Detach and reattach a tmux session?
**A:** `Ctrl+b, d` → detach, `tmux attach -t session_name` → reattach

**Q4:** Split tmux window into panes?
**A:** `Ctrl+b, %` → vertical, `Ctrl+b, "` → horizontal

---

## ✅ **Tips for Interviews**

* **Know basic + advanced commands:** `ls`, `grep`, `awk`, `sed`, `find`, `ps`, `top`, `df`, `du`
* **Understand permissions & security**: SUID, SGID, sticky bits, ACLs, sudo
* **Practice Docker commands** and Dockerfile basics
* **Know terminal multiplexers** for remote servers
* **Be able to troubleshoot:** logs, memory, CPU, disk, network issues

---
