# Linux Command Line Basics

Beginner-friendly Linux terminal notes with clear command explanations and examples.

---

## What is Linux?

- **Operating System (OS)** examples: Windows, macOS, Linux.
- **Linux kernel**: the core part of the OS.
- It connects software (applications) to hardware (CPU, RAM, disk, devices).

## Terminal & Shell

- **Terminal**: the program/window where you type commands.
- **Shell**: the command interpreter (user interface) that interacts with the OS.
- Common shells: `bash`, `zsh`
- Prompt symbols:
    - `$` normal user
    - `#` root (administrator)

---

## Basic Commands (Essentials)

### Where am I?

- `pwd` — print working directory (shows your current location)

### List files and folders

- `ls` — list directory contents
    - `ls -a` show hidden files
    - `ls -l` long format
    - `ls -la` hidden + long format

### Move between directories

- `cd <dir>` — change directory
    - `cd Desktop`
    - `cd ..` go up one directory
    - `cd -` go back to the previous directory
    - `cd ~` go to home directory
    - `cd /` go to root directory

### Clear the terminal

- `clear` — clears the terminal screen

### Who am I?

- `whoami` — shows the current user

### View file content

- `cat file.txt` — print file content
- `more file.txt` / `less file.txt` — view long files page by page

 ---
### Create

- `touch file.txt` — create an empty file
- `mkdir folder` — create a directory

  ```
#  Writing to Files in Linux (Terminal Guide)

A clear, hands-on reference guide on how to create, overwrite, append, and edit files directly from the Linux command line using redirection operators, `cat`, and text editors.

---

## Quick Reference

| Method / Tool | Action | Command / Syntax |
| :--- | :--- | :--- |
| **`>` (Single Redirect)** | Create or Overwrite file | `echo "Hello" > file.txt` |
| **`>>` (Double Redirect)** | Append text to end of file | `echo "New line" >> file.txt` |
| **`cat << EOF`** | Write multi-line blocks | `cat << EOF > file.txt` |
| **`nano`** | Open beginner-friendly text editor | `nano file.txt` |
| **`vim`** | Open advanced text editor | `vim file.txt` |

---

##  Detailed Guide

### 1. Using Redirection Operators (`>` and `>>`)
Redirection operators take the output of a command (like `echo`) and save it directly into a file instead of displaying it on your screen.

#### A. Overwrite or Create a New File (`>`)
The single greater-than sign (`>`) creates a new file if it doesn't exist, or **overwrites** all existing content if the file already exists.
```bash
echo "Hello, World!" > myfile.txt

```

* *Result:* Creates `myfile.txt` containing `Hello, World!`. If the file already existed, its previous contents are completely erased.

#### B. Append to an Existing File (`>>`)

The double greater-than sign (`>>`) adds new text to the **end** of a file without deleting what is already there.

```bash
echo "This is a second line." >> myfile.txt

```

* *Result:* Adds the text to a new line at the bottom of `myfile.txt`, keeping the old content safe.

---

### 2. Writing Multi-Line Text (`cat` with EOF)

If you want to write a multi-line block of text into a file quickly without opening an editor, you can use `cat` combined with an End-Of-File (`EOF`) marker:

```bash
cat << EOF > config.txt
server_ip = 127.0.0.1
port = 3000
status = active
EOF

```

* *Result:* Everything between the two `EOF` markers is written cleanly into `config.txt` as a multi-line configuration file.

---

### 3. Using Terminal Text Editors (`nano` or `vim`)

If you prefer an interactive text editor to write, edit, or format text documents:

* **Using `nano` (Beginner-friendly):**
```bash
nano notes.txt

```


* *How to save & exit:* Type your text, press `Ctrl + O` then `Enter` to save, and `Ctrl + X` to exit.


* **Using `vim` (Advanced):**
```bash
vim notes.txt

```


* *How to save & exit:* Press `i` to start typing, press `Esc` when finished, then type `:wq` and hit `Enter` to save and quit.



---

### Copy

- `cp src dst` — copy file (e.g. `cp file1.txt backup.txt`)
- `cp -r dir1 dir2` — copy directory recursively

### Move / rename

- `mv src dst` — move or rename (e.g. `mv old.txt new.txt`)

### Remove (be careful)

- `rm file.txt` — remove file
- `rmdir folder` — remove empty directory
- `rm -r folder` — remove directory (recursive)
- `rm -rf folder` — force remove ⚠️ dangerous

---

## Linux Directories (Very Important)

- `/home` — users' home directories
- `/root` — root user home directory
- `/bin` — essential user commands (binaries)
- `/sbin` — system/admin commands
- `/etc` — system configuration files
- `/var` — variable data (logs, cache, spool)
- `/tmp` — temporary files
- `/dev` — devices (disks, terminals, etc.)

---

## Identity, Users, and Groups

### User / group IDs

- `id` — shows UID, primary group (GID), and secondary groups

### Hostname

- `hostname` — machine name on the network

### User management (admin)

> Requires admin/root permissions (`sudo`).
> 
- `sudo <command>` — run command with administrator rights
- `adduser <name>` — create a new user (Debian/Ubuntu)
- `userdel <name>` — delete a user
- `passwd` — change password
- `chsh` — change login shell
- `cat /etc/passwd` — list users (system + normal)
- `cat /etc/shadow` — password hashes (root only)
- `chmod` — change file/directory permissions
---
#  Linux Text Processing & Filtering Toolkit

A handy quick-reference cheat sheet for searching, parsing, transforming, and decoding file contents using powerful command-line utilities.

---

##  Quick Reference Table

| Tool | Primary Function | Common Syntax / Example |
| --- | --- | --- |
| **`grep`** | Pattern searching within files | `grep -r "error" /var/log/` |
| **`cut`** | Extract specific fields/columns | `cut -d':' -f1 /etc/passwd` |
| **`awk`** | Field processing & pattern matching | `awk '{print $1}' file.txt` |
| **`sort`** | Reorder lines alphabetically/numerically | `sort -n data.txt` |
| **`uniq`** | Deduplicate consecutive identical lines | `sort file.txt |
| **`tr`** | Translate or delete characters | `cat file.txt |
| **`strings`** | Extract printable strings from binary files | `strings /bin/ls` |
| **`base64`** | Base64 data encoding/decoding | `echo -n "hello" |

---

##  Detailed Tool Guide

### 1. `grep` — Pattern Searching

Searches for specific patterns, words, or regular expressions within files.

```bash
# Recursively search for the word "error" in the /var/log directory
grep -r "error" /var/log/

```

### 2. `cut` — Field Extraction

Extracts specific sections (columns or fields) from each line of a file.

```bash
# Extract the first field (username) from /etc/passwd using ':' as a delimiter
cut -d':' -f1 /etc/passwd

```


### 3. `sort` — Sorting Lines

Rearranges the lines of text files in alphabetical or numerical order.

```bash
# Sort numerical data numerically (-n)
sort -n data.txt

```

### 4. `uniq` — Removing Duplicates

Filters out consecutive duplicate lines. (Usually paired with `sort`).

```bash
# Sort the file and count occurrences of each unique line
sort file.txt | uniq -c

```

### 5. `tr` — Character Translation

Translates, squeezes, and/or deletes characters from standard input.

```bash
# Convert lowercase letters to uppercase
cat file.txt | tr 'a-z' 'A-Z'

```

### 6. `strings` — Binary String Extraction

Dumps printable character strings from binary files.

```bash
# Extract human-readable text from a binary executable
strings /bin/ls

```

### 7. `base64` — Encoding & Decoding

Encodes or decodes data into/from Base64 representation.

```bash
#, Encode a string into Base64 format
echo -n "hello" | base64

# Decode Base64 string back to plaintext
echo "aGVsbG8=" | base64 --decode

```

#  File Permissions & Redirection (`chmod`)

A quick-reference guide on how to manage file permissions using symbolic modes in Linux.

---

##  Quick Reference

| Command | Primary Function | Example / Syntax |
| --- | --- | --- |
| **`chmod`** | Change file/directory permissions using letters and operators | `chmod +x script.sh` |

---

## Detailed Guide

### What Do the Permissions Mean?

A permission string looks like `rwx rwx rwx` and applies to three categories of users:

1. **Owner (`u`)**: The user who owns the file.
2. **Group (`g`)**: Users assigned to the same group as the file.
3. **Others (`o`)**: Everyone else on the system.

* **`r` (Read):** View file contents or list a directory's contents.
* **`w` (Write):** Modify or delete the file/directory.
* **`x` (Execute):** Run the file as a program/script or enter a directory.

---

### The Symbolic Syntax

The symbolic method uses letters to target specific users and operators to add or remove permissions.

* **Targets:** `u` (owner), `g` (group), `o` (others), `a` (all)
* **Operators:** `+` (add permission), `-` (remove permission), `=` (set exact permission)

**Example:**

```bash
chmod +x script.sh

```

* **Explanation:** Adds (`+`) execute (`x`) permission for everyone on `script.sh`.

---

### When and How to Execute It?

#### **When should you use it?**

* **When you write a new script:** If you write a Bash script and try to run it immediately, Linux blocks you with a `Permission denied` error until you make it executable.
* **When installing custom binaries:** If you download a program or binary file and it won't run, you likely need to grant execution rights.

#### **How to execute the file after changing permissions?**

Once you have granted execution rights, run the file in your terminal by specifying its path:

```bash
# If the script is in your current directory:
./script.sh

# Or by providing the full path:
/home/username/projects/script.sh

```

---

> [!NOTE]
> You must either **own the file** or have **administrator privileges (`sudo`)** to change its permissions using `chmod`.


---
 
#  File Compression & Decompression Reference Guide

A clean, focused reference guide for handling archives, single-file compression, and decompression in the Linux terminal.

---

##  Quick Reference

| Format / Tool | Task | Command / Syntax |
| :--- | :--- | :--- |
| **`.tar`** (Standard Archive) | Compress / Bundle | `tar -cvf archive.tar dir/` |
| | Decompress / Extract | `tar -xvf archive.tar` |
| **`.tar.gz`** (Gzip Archive) | Compress / Bundle | `tar -zcvf archive.tar.gz dir/` |
| | Decompress / Extract | `tar -zxvf archive.tar.gz` |
| **`.tar.bz2`** (Bzip2 Archive) | Compress / Bundle | `tar -jcvf archive.tar.bz2 dir/` |
| | Decompress / Extract | `tar -jxvf archive.tar.bz2` |
| **`.gz`** (Single Gzip File) | Compress | `gzip file.txt` |
| | Decompress | `gunzip file.txt.gz` (or `gzip -d`) |
| **`.bz2`** (Single Bzip2 File) | Compress | `bzip2 file.txt` |
| | Decompress | `bunzip2 file.txt.bz2` (or `bzip2 -d`) |

---

##  Detailed Guide

### 1. Archive Management (`tar`)
The `tar` utility bundles multiple files and folder structures into a single file.

#### Creating Archives
* **Standard `.tar` (Uncompressed):**
  ```bash
  tar -cvf archive.tar dir/

```

* **Gzipped `.tar.gz` (Compressed):**
```bash
tar -zcvf archive.tar.gz dir/

```


* **Bzipped `.tar.bz2` (High Compression):**
```bash
tar -jcvf archive.tar.bz2 dir/

```



#### Extracting / Decompressing Archives

* **Extract Standard `.tar`:**
```bash
tar -xvf archive.tar

```


* **Extract `.tar.gz`:**
```bash
tar -zxvf archive.tar.gz

```


* **Extract `.tar.bz2`:**
```bash
tar -jxvf archive.tar.bz2

```
---

### 2. Single-File Compression & Decompression

Unlike `tar` (which combines multiple files), these tools compress **individual files** to save disk space.

#### Using `gzip` (`.gz`)

* **Compress a file:**
```bash
gzip file.txt
# Result: file.txt.gz (replaces original)

```


* **Decompress a file:**
```bash
gunzip file.txt.gz
# Alternative: gzip -d file.txt.gz

```



#### Using `bzip2` (`.bz2`)

* **Compress a file (higher compression ratio):**
```bash
bzip2 file.txt
# Result: file.txt.bz2 (replaces original)

```


* **Decompress a file:**
```bash
bunzip2 file.txt.bz2
# Alternative: bzip2 -d file.txt.bz2

```
## Networking (basics)

- `ifconfig` (legacy) / `ip a` (modern) — network interfaces and IP addresses

### Network Interface Details (from `ifconfig`)

- **MAC address** — unique hardware address of the network card (e.g. `08:00:27:da:bb:d9`)
- **Netmask** — defines the size of the local network (e.g. `255.255.255.0` → up to 254 usable host IPs)
- **Broadcast address** — send to all devices on the same network (e.g. `10.0.2.255`)
- **RX / TX** — received (RX) and transmitted (TX) data totals

---
#  Network Tools, Sockets, & Scanning Lab

A comprehensive guide and hands-on workshop explaining essential command-line networking tools (`nc`, `nmap`, `openssl`) and how to interact with network services using automated scripts.

---

##  Quick Reference

| Tool | Primary Purpose | Common Syntax / Example |
| :--- | :--- | :--- |
| **Netcat (`nc`)** | Port scanning, listening, and raw TCP/UDP connections | `nc -zv 192.168.1.1 80` |
| **Nmap (`nmap`)** | Network discovery, port scanning, and service auditing | `nmap -sV -sC target.com` |
| **OpenSSL (`openssl`)** | Testing and debugging SSL/TLS secure connections | `openssl s_client -connect example.com:443` |
| **Socket Loop** | Automated testing or brute-forcing over a network socket | `for pin in {0000..9999}; do echo "$pin" \| nc ...; done` |

---

## Detailed Tool Explanations

### 1. Netcat (`nc`) — The Networking "Swiss Army Knife"
Netcat is a versatile utility used to read and write data across network connections using TCP or UDP protocols.

* **Checking if a port is open (`-zv`):**
  ```bash
  nc -zv <host> <port>

```

* **`-z`**: Zero-I/O mode (used purely for scanning, without sending actual data).
* **`-v`**: Verbose mode (gives detailed output on whether the connection succeeded or failed).
* **Starting a local listener (`-lvp`):**
```bash
nc -lvp <port>

```


* **`-l`**: Listen mode (sets Netcat up as a server waiting for incoming connections).
* **`-v`**: Verbose mode (shows who connected).
* **`-p`**: Specifies the local port to listen on.



---

### 2. Nmap (`nmap`) — Network Mapper & Security Auditing

Nmap is the industry-standard tool for network exploration, port scanning, and vulnerability detection.

* **Service version and default script scan:**
```bash
nmap -sV -sC <target>

```


* **`-sV`**: Probe open ports to determine service/version info (e.g., discovering what software/version is running).
* **`-sC`**: Runs a default set of safe, helpful scripting engine (NSE) scripts to gather extra information (like HTTP headers or SSL ciphers).



---

### 3. OpenSSL (`openssl`) — TLS/SSL Connection Debugging

OpenSSL is a cryptography toolkit. Its `s_client` subcommand lets you act as a raw TLS client to inspect secure web servers.

* **Connecting over an SSL/TLS wrapper:**
```bash
openssl s_client -connect <host>:443

```


* *Use case:* Checking SSL certificate expiration dates, inspecting certificate chains, and debugging handshake errors.



---

### 4. Socket Loop Example — Automation via Shell Scripting

You can combine standard Bash loops with networking tools like Netcat to automate repetitive tasks against a network socket.

* **The Example:**
```bash
for pin in {0000..9999}; do echo "$pin" | nc 127.0.0.1 3000; done

```


* *How it works:* Generates sequential inputs (`0000` to `9999`) and pipes them directly into a target network socket.



---

## 🛠️ Hands-On Practice Lab

Follow these steps to test every tool locally on your machine using safe, self-contained environments.

> **Setup Tip:** Open **two separate terminal windows or tabs** to run these exercises:
> * **Terminal A:** Acts as our "Server" (listener).
> * **Terminal B:** Acts as our "Client" (sender/scanner).
> 
> 

---

### Lab 1: Netcat (`nc`) Communication

1. **Start a Local Listener (Terminal A):**
```bash
nc -lvp 4444

```


2. **Connect and Send Data (Terminal B):**
```bash
nc 127.0.0.1 4444

```


*(Type any message in Terminal B and press Enter—watch it appear in Terminal A!)*
3. **Scan the Port (Terminal B):**
```bash
nc -zv 127.0.0.1 4444

```


*(Expected output: `Connection to 127.0.0.1 4444 port [tcp/*] succeeded!`)*

---

### Lab 2: Nmap Local Audit (`nmap`)

Scan your local loopback interface to test service detection:

```bash
nmap -sV -sC 127.0.0.1

```

---

### Lab 3: Secure Connection Debugging (`openssl`)

Connect to a public TLS server to inspect its security certificate:

```bash
openssl s_client -connect google.com:443

```

* *Interactive trick:* Once connected, type `GET / HTTP/1.1` and press **Enter twice** to view the raw HTTP response from the server.

---

### Lab 4: Automated Socket Loop

1. **Start a Listener (Terminal A):**
```bash
nc -lvp 3000

```


2. **Run the Automated Loop (Terminal B):**
```bash
for pin in {0000..0005}; do echo "Trying PIN: $pin" | nc 127.0.0.1 3000; sleep 1; done

```


*(Watch Terminal A receive each sequential input automatically with a 1-second delay!)*

---

## Find help

- `man <command>` — manual page (e.g. `man ls`)
- `apropos <keyword>` — search for commands by keyword
- `which <command>` — shows the path of a command (e.g. `which python`)

---

## Storage

- `lsblk` — list disks and partitions

## Mounting

- `mount` — show mounted filesystems
- `mount <device> <mount_point>` — manual mounting (admin)

---


## Processes & System Monitoring

### List processes

- `ps aux` — list running processes
- `top` — live process view (CPU/RAM)

### Kill a process

- `kill <PID>` — stop a process (sends `SIGTERM`)
- `kill -9 <PID>` — force stop (`SIGKILL`)
- `pkill <name>` — kill a process by name
- `kill -l` — list available signals

### Find a PID

- `ps aux | grep <name>`
- `pgrep <name>` (if available)

---

## Job Control

- `Ctrl+Z` — suspend (pause) the currently running process
- `jobs` — list suspended/background jobs
- `fg %1` — bring job 1 back to the foreground
- `bg %1` — resume job 1 in the background
- `Ctrl+C` — interrupt/kill the currently running process
- `pstree` — display running processes as a tree (parent → children)

> Tip: job control (`jobs`, `fg`, `bg`) is for processes started in *your current terminal session*.
> 

---

## systemd (Services / Daemons)

A **daemon** is a background program that runs without a visible interface. `systemd` is the main service manager on many Linux distros.

- `systemctl status <service>`
- `systemctl start <service>`
- `systemctl stop <service>`
- `systemctl enable <service>` — start at boot
- `systemctl disable <service>`
- `systemctl list-units`

**Unit types:**

- `service` — background service
- `socket` — socket activation
- `timer` — scheduled unit
- `target` — grouping unit (boot goals)

---

## SSH (Remote Access)

- `ssh user@host` — connect (e.g. `ssh ayoub@192.168.1.100`)
- `ssh -p 2222 user@host` — custom port
- `ssh -i ~/.ssh/key.pem user@host` — use a private key

---

## Package Managers

### apt (Debian/Ubuntu)

- `sudo apt update` — refresh package lists
- `sudo apt install <package>`
- `sudo apt remove <package>`
- `sudo apt upgrade` — upgrade installed packages

### snap

- `snap find <app>`
- `sudo snap install <app>`
- `snap list`

---

## Terminal Shortcuts

- `Ctrl+U` — delete everything before the cursor
- `Ctrl+K` — delete everything after the cursor
- `Ctrl+Y` — paste back what was just deleted
- `Ctrl+A` — jump to beginning of the line
- `Ctrl+E` — jump to end of the line

### Aliases

- `alias name="command"` — create a shortcut for a longer command
- Make it permanent by adding it to `~/.bashrc` (or `~/.zshrc`) then run `source ~/.bashrc`

---

## Understanding the Prompt

- `$` — normal user
- `#` — root (administrator)

> If you see `#`, commands run with full admin privileges (no `sudo` needed) — mistakes can be much more dangerous.
> 

# **Done By AYOUB BOUAYAD**
