# 💻 Installing Ubuntu, WSL & Terminal

> [!NOTE]
> **Module 3 • Lesson 2**
>
> Learn how to install Ubuntu using Windows Subsystem for Linux (WSL), understand the terminal, and prepare your system for bioinformatics analysis.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand what WSL is.
- Install Ubuntu on Windows.
- Open and use the Linux terminal.
- Verify your Linux installation.
- Understand why WSL is widely used in bioinformatics.

---

# 📚 Prerequisites

Before starting this lesson, you should know:

- Basic computer usage
- What Linux is (Lesson 1)

---

# 💡 Real-Life Analogy

Imagine you own a Windows laptop but need to work in a Linux laboratory.

Instead of buying another computer,

WSL creates a **Linux laboratory inside your Windows system**.

You can run Linux commands and bioinformatics software without leaving Windows.

---

# 📌 What is WSL?

**Windows Subsystem for Linux (WSL)** is a feature that allows Linux distributions such as Ubuntu to run directly on Windows.

It enables users to execute Linux commands, install bioinformatics tools, and perform NGS analysis without using a virtual machine.

---

# ❓ Why Use WSL?

Advantages:

- No dual boot required.
- Better performance than most virtual machines.
- Low memory usage.
- Direct access to Linux tools.
- Easy file sharing between Windows and Linux.
- Supports Conda, Docker, Python, R, and most bioinformatics software.

---

# 📊 WSL at a Glance

| Feature | Description |
|---------|-------------|
| Full Linux Command Line | ✅ |
| Runs Inside Windows | ✅ |
| Requires Separate Partition | ❌ |
| Bioinformatics Compatible | ✅ |
| GPU Support (supported workflows) | ✅ |

---

# 🖥️ Installing WSL

Open **Windows PowerShell as Administrator** and run:

```powershell
wsl --install
```

This command:

- Enables WSL.
- Downloads the default Linux distribution (usually Ubuntu).
- Installs the Linux kernel.
- Configures the environment.

Restart your computer if prompted.

---

# 🐧 Installing Ubuntu

If Ubuntu is not installed automatically:

Open Microsoft Store

↓

Search

```
Ubuntu
```

↓

Install

```
Ubuntu 24.04 LTS
```

Launch Ubuntu from the Start Menu.

---

# 🔐 First-Time Setup

When Ubuntu starts for the first time:

Create:

```
Username
```

Example

```
sai
```

Create a password.

> **Note:** The password will not be visible while typing in the terminal. This is normal behavior in Linux.

---

# 📌 Opening the Terminal

Ways to open Ubuntu Terminal:

- Start Menu → Ubuntu
- Windows Terminal → Ubuntu Profile
- Command Prompt

```cmd
wsl
```

---

# 💻 First Commands

## Check Current User

```bash
whoami
```

Example Output

```text
sai
```

---

## Check Current Directory

```bash
pwd
```

Example Output

```text
/home/sai
```

---

## List Files

```bash
ls
```

---

## Check Linux Version

```bash
cat /etc/os-release
```

Example Output

```text
Ubuntu 24.04 LTS
```

---

## Check Kernel Version

```bash
uname -r
```

Example Output

```text
6.x.x
```

---

## Check Available Memory

```bash
free -h
```

---

## Check Disk Space

```bash
df -h
```

---

## Check CPU Information

```bash
lscpu
```

---

# 📂 Access Windows Files

Windows drives are mounted under:

```text
/mnt
```

Example:

```text
/mnt/c

/mnt/d

/mnt/e
```

Navigate to the C drive:

```bash
cd /mnt/c
```

Navigate to the Desktop:

```bash
cd /mnt/c/Users/YourUser/Desktop
```

Replace **YourUser** with your Windows username.

---

# 📂 Access Linux Files from Windows

Linux files are stored inside WSL.

To open the current Linux directory in Windows File Explorer:

```bash
explorer.exe .
```

The `.` represents the current directory.

---

# 📊 Recommended Folder Structure

```text
/home/sai/

├── Bioinformatics/
│
├── Projects/
│
├── Downloads/
│
├── Conda_Environments/
│
└── Scripts/
```

---

# 🧬 Bioinformatics Example

Create a project folder:

```bash
mkdir RNASeq_Project
```

Move into the project:

```bash
cd RNASeq_Project
```

Check the current location:

```bash
pwd
```

Expected Output

```text
/home/sai/RNASeq_Project
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Installing tools in the Windows Command Prompt instead of Ubuntu.
> - Saving projects in random folders.
> - Forgetting your Linux username.
> - Confusing Windows paths (`C:\Users\...`) with Linux paths (`/home/...`).

---

# 🧠 Interview Corner

### ❓ What is WSL?

Windows Subsystem for Linux allows Linux to run directly on Windows without a traditional virtual machine.

---

### ❓ Why is WSL popular in Bioinformatics?

Because it provides a Linux environment while allowing users to continue using Windows, making it easier to run bioinformatics software and workflows.

---

### ❓ Where are Windows drives located in Linux?

Inside the `/mnt` directory (for example, `/mnt/c`).

---

### ❓ How do you open the current Linux folder in Windows?

```bash
explorer.exe .
```

---

# 📝 Lesson Summary

- WSL allows Linux to run inside Windows.
- Ubuntu is one of the most commonly used Linux distributions for bioinformatics.
- The terminal is the primary interface for running bioinformatics tools.
- Windows drives are available under `/mnt`.
- Linux directories can be opened in Windows using `explorer.exe .`.

---

# 💪 Practice Exercises

## Exercise 1

Display your username.

```bash
whoami
```

---

## Exercise 2

Display your current directory.

```bash
pwd
```

---

## Exercise 3

Check your Ubuntu version.

```bash
cat /etc/os-release
```

---

## Exercise 4

Open the current Linux folder in Windows Explorer.

```bash
explorer.exe .
```

---

## Exercise 5

Create a practice folder.

```bash
mkdir Linux_Practice
```

---

# ⚡ Quick Revision

| Question | Answer |
|----------|--------|
| What is WSL? | Windows Subsystem for Linux |
| Default Ubuntu Home? | `/home/username` |
| Windows Drives? | `/mnt/c`, `/mnt/d` |
| Current Directory? | `pwd` |
| Current User? | `whoami` |
| Open Folder in Windows? | `explorer.exe .` |

---

# 📚 References

- Ubuntu Documentation
- Microsoft WSL Documentation
- GNU Project

---

# ➡️ Next Lesson

**Navigating Directories (pwd, ls, cd)**
