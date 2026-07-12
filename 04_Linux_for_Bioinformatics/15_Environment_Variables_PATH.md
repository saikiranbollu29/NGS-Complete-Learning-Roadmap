# 🌍 Environment Variables, PATH & Software Installation

> [!NOTE]
> **Module 3 • Lesson 15**
>
> Learn how Linux finds programs, manages environment variables, and configures your system for bioinformatics software.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand environment variables.
- Understand the PATH variable.
- Use `export`.
- Reload `.bashrc`.
- Install and use bioinformatics software correctly.
- Troubleshoot "command not found" errors.

---

# 📚 Prerequisites

- Linux Navigation
- Searching Files
- Downloading Files

---

# 💡 Real-Life Analogy

Imagine a hospital.

Every department has its own location.

When someone asks for

```
PCR Machine
```

the staff immediately knows where it is.

Linux works the same way.

The **PATH** variable is like a hospital directory.

When you type

```bash
fastqc
```

Linux searches every folder listed in PATH until it finds the program.

---

# 📌 What are Environment Variables?

Environment variables are special variables that store information about your Linux environment.

Examples include:

- Your username
- Home directory
- Current shell
- Language
- PATH

---

# 📌 View All Environment Variables

```bash
printenv
```

or

```bash
env
```

Example Output

```text
HOME=/home/sai

USER=sai

PATH=/usr/local/bin:/usr/bin:/bin
```

---

# 📌 Display a Specific Variable

Example:

```bash
echo $HOME
```

Output

```text
/home/sai
```

---

Display username.

```bash
echo $USER
```

---

Display shell.

```bash
echo $SHELL
```

---

Display PATH.

```bash
echo $PATH
```

Example

```text
/usr/local/bin:/usr/bin:/bin:/home/sai/miniconda3/bin
```

---

# 📌 What is PATH?

PATH is a list of directories where Linux searches for executable programs.

When you type

```bash
fastqc
```

Linux checks every directory in PATH until it finds the FastQC executable.

---

# 📊 How PATH Works

```text
You type:

fastqc

↓

Linux checks

/usr/local/bin

↓

Not found

↓

/usr/bin

↓

Not found

↓

/home/sai/miniconda3/bin

↓

Found

↓

Program Executes
```

---

# 📌 Check Where a Program Is Installed

```bash
which fastqc
```

Example Output

```text
/home/sai/miniconda3/envs/ngs/bin/fastqc
```

---

# 📌 Temporary Environment Variable

Create a variable.

```bash
export PROJECT=RNASeq_Project
```

Check it.

```bash
echo $PROJECT
```

Output

```text
RNASeq_Project
```

This variable exists only for the current terminal session.

---

# 📌 Add a Directory to PATH (Temporary)

Example:

```bash
export PATH=$PATH:/home/sai/tools
```

Verify:

```bash
echo $PATH
```

---

# 📌 Make PATH Permanent

Open the `.bashrc` file.

```bash
nano ~/.bashrc
```

Add:

```bash
export PATH=$PATH:/home/sai/tools
```

Save:

```
CTRL + O

ENTER

CTRL + X
```

Reload the file.

```bash
source ~/.bashrc
```

Now the PATH change will be available in every new terminal session.

---

# 📌 What is `.bashrc`?

`.bashrc` is a configuration file that runs every time a new Bash terminal starts.

It is commonly used to:

- Set environment variables
- Update PATH
- Create aliases
- Activate tools automatically

---

# 📌 What Does `source` Do?

The `source` command reloads a configuration file without closing the terminal.

Example:

```bash
source ~/.bashrc
```

Without `source`, you would need to close and reopen the terminal.

---

# 🧬 Bioinformatics Examples

## Check BWA

```bash
which bwa
```

---

## Check Samtools

```bash
which samtools
```

---

## Check FastQC

```bash
which fastqc
```

---

## Check Python

```bash
which python
```

---

## Display Conda Installation Path

```bash
echo $PATH
```

---

# 🧬 NGS Workflow Connection

Suppose you install FastQC using Conda.

Verify the installation.

```bash
which fastqc
```

Output

```text
/home/sai/miniconda3/envs/ngs/bin/fastqc
```

Run the program.

```bash
fastqc --version
```

If Linux returns

```text
command not found
```

Check:

```bash
echo $PATH
```

or

```bash
which fastqc
```

---

# 🧬 Interview Lab

### Scenario

You installed BWA.

Typing

```bash
bwa
```

returns

```text
command not found
```

---

### Step 1

Locate BWA.

```bash
find ~/ -name bwa
```

---

### Step 2

Check PATH.

```bash
echo $PATH
```

---

### Step 3

Add the directory containing `bwa` to PATH.

```bash
export PATH=$PATH:/home/sai/tools/bwa
```

---

### Step 4

Run

```bash
bwa
```

---

# 📊 Important Environment Variables

| Variable | Meaning |
|-----------|---------|
| `$HOME` | Home directory |
| `$USER` | Current user |
| `$PATH` | Search path for programs |
| `$SHELL` | Current shell |
| `$PWD` | Current directory |

---

# 💪 Practice Exercises

## Exercise 1

Display HOME.

```bash
echo $HOME
```

---

## Exercise 2

Display PATH.

```bash
echo $PATH
```

---

## Exercise 3

Create a variable.

```bash
export PROJECT=WGS_Project
```

---

## Exercise 4

Print it.

```bash
echo $PROJECT
```

---

## Exercise 5

Reload `.bashrc`.

```bash
source ~/.bashrc
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Overwriting PATH accidentally with `export PATH=/new/path` instead of appending using `export PATH=$PATH:/new/path`.
> - Forgetting to reload `.bashrc` after making changes.
> - Editing the wrong shell configuration file.
> - Ignoring `which` when troubleshooting "command not found".

---

# 🧠 Interview Corner

### ❓ What is PATH?

A list of directories that Linux searches when executing commands.

---

### ❓ What does `export` do?

It creates or updates environment variables for the current shell session.

---

### ❓ Why use `source ~/.bashrc`?

To reload configuration changes without restarting the terminal.

---

### ❓ Why does "command not found" occur?

Usually because the executable is not installed or its directory is not included in the PATH.

---

### ❓ How do you check where FastQC is installed?

```bash
which fastqc
```

---

# 📝 Lesson Summary

- Environment variables store system information.
- PATH tells Linux where to find executable programs.
- `export` creates or modifies environment variables.
- `.bashrc` stores shell configuration.
- `source` reloads configuration files.
- Correct PATH configuration is essential for running bioinformatics software.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `printenv` | Show all environment variables |
| `echo $PATH` | Display PATH |
| `echo $HOME` | Show home directory |
| `export VAR=value` | Create environment variable |
| `export PATH=$PATH:/new/path` | Add to PATH |
| `which bwa` | Find executable |
| `source ~/.bashrc` | Reload configuration |

---

# 📚 References

- GNU Bash Manual
- Ubuntu Documentation
- Conda Documentation
- Bioinformatics Data Skills (Book)

---

# ➡️ Next Lesson

**Bash Scripting for Bioinformatics (`bash`, variables, loops, functions)**
