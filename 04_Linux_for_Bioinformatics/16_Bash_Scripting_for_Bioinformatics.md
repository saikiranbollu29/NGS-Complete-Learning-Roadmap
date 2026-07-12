# 🤖 Bash Scripting for Bioinformatics

> [!NOTE]
> **Module 3 • Lesson 16**
>
> Learn how to automate repetitive bioinformatics tasks using Bash scripts. This lesson introduces variables, loops, conditionals, functions, and real NGS automation examples.

---

# 🎯 Learning Objectives

After completing this lesson, you will be able to:

- Understand Bash scripts.
- Write and execute shell scripts.
- Use variables.
- Accept user input.
- Use loops and conditional statements.
- Create reusable functions.
- Automate NGS workflows.

---

# 📚 Prerequisites

- Linux Basics
- File Management
- grep
- awk
- sed
- PATH
- chmod

---

# 💡 Real-Life Analogy

Imagine a sequencing laboratory.

You receive **500 FASTQ files**.

Would you manually type:

```bash
fastqc sample1.fastq.gz

fastqc sample2.fastq.gz

fastqc sample3.fastq.gz
```

500 times?

Of course not.

Instead,

you write one Bash script.

The computer repeats the task automatically.

---

# 📌 What is a Bash Script?

A Bash script is a text file containing Linux commands that are executed automatically.

Instead of typing commands repeatedly,

you save them in a file.

Example

```
run_pipeline.sh
```

---

# 📌 Why Use Bash in Bioinformatics?

Almost every bioinformatics workflow contains repetitive tasks:

- Run FastQC on hundreds of samples.
- Align many FASTQ files.
- Rename sequencing files.
- Count variants.
- Generate reports.
- Organize results.

Bash automates all of these.

---

# 📌 Creating Your First Script

Create a file.

```bash
nano hello.sh
```

Type:

```bash
#!/bin/bash

echo "Hello Bioinformatics!"
```

Save:

```
CTRL + O

ENTER

CTRL + X
```

---

# 📌 Make the Script Executable

```bash
chmod +x hello.sh
```

---

# 📌 Run the Script

```bash
./hello.sh
```

Output

```text
Hello Bioinformatics!
```

---

# 📌 Understanding the Shebang

Every Bash script should begin with:

```bash
#!/bin/bash
```

This tells Linux to execute the script using the Bash shell.

---

# 📌 Variables

Variables store values.

Example

```bash
#!/bin/bash

sample="Sample01"

echo $sample
```

Output

```text
Sample01
```

---

# Multiple Variables

```bash
project="RNASeq"

reference="GRCh38"

threads=8
```

Display

```bash
echo $project

echo $reference

echo $threads
```

---

# 📌 User Input

```bash
#!/bin/bash

echo "Enter sample name:"

read sample

echo "Processing $sample"
```

---

# 📌 Command Line Arguments

Instead of typing input,

pass arguments.

Script

```bash
#!/bin/bash

echo $1
```

Run

```bash
./script.sh Sample01
```

Output

```text
Sample01
```

---

## Common Argument Variables

| Variable | Meaning |
|----------|---------|
| `$0` | Script name |
| `$1` | First argument |
| `$2` | Second argument |
| `$#` | Number of arguments |
| `$@` | All arguments |

---

# 📌 if Statement

```bash
#!/bin/bash

if [ -f sample.fastq.gz ]
then
    echo "File exists."
else
    echo "File not found."
fi
```

---

# 📌 for Loop

Process multiple FASTQ files.

```bash
for sample in *.fastq.gz
do
    echo $sample
done
```

---

# Real Bioinformatics Example

Run FastQC on all FASTQ files.

```bash
for sample in *.fastq.gz
do
    fastqc "$sample" -o qc/
done
```

---

# 📌 while Loop

```bash
count=1

while [ $count -le 5 ]
do
    echo $count
    count=$((count+1))
done
```

---

# 📌 Functions

```bash
greet(){

echo "Welcome to Bioinformatics"

}

greet
```

---

# Function with Arguments

```bash
run_fastqc(){

fastqc "$1" -o qc/

}
```

Use

```bash
run_fastqc sample.fastq.gz
```

---

# 📌 Comments

```bash
# This is a comment.
```

Always document your scripts.

---

# 🧬 Mini Bioinformatics Lab

Create the project.

```text
RNASeq_Project/

raw_data/

qc/

scripts/
```

Move into scripts.

```bash
cd scripts
```

Create

```bash
nano run_fastqc.sh
```

Paste

```bash
#!/bin/bash

mkdir -p ../qc

for sample in ../raw_data/*.fastq.gz
do
    echo "Running FastQC on $sample"
    fastqc "$sample" -o ../qc
done

echo "FastQC completed."
```

Save and exit.

---

Make executable.

```bash
chmod +x run_fastqc.sh
```

Run

```bash
./run_fastqc.sh
```

---

# Expected Workflow

```text
raw_data/

↓

Loop through FASTQ files

↓

Run FastQC

↓

Save reports

↓

Finished
```

---

# 📌 Error Handling

Check if FASTQ files exist.

```bash
#!/bin/bash

if ls *.fastq.gz 1> /dev/null 2>&1
then
    echo "FASTQ files found."
else
    echo "No FASTQ files found."
fi
```

---

# 🧬 NGS Workflow Connection

Example automation pipeline.

```bash
#!/bin/bash

mkdir -p qc

for sample in raw_data/*.fastq.gz
do
    fastqc "$sample" -o qc
done

multiqc qc -o qc_report
```

Instead of running FastQC manually for every file,

the script processes all files automatically.

---

# 🧬 Interview Lab

### Scenario

You receive

```text
sample1_R1.fastq.gz

sample2_R1.fastq.gz

sample3_R1.fastq.gz

...

sample200_R1.fastq.gz
```

Write a Bash script to perform FastQC on every sample.

Solution

```bash
#!/bin/bash

mkdir -p qc

for sample in *.fastq.gz
do
    fastqc "$sample" -o qc
done
```

---

# 💪 Practice Exercises

## Exercise 1

Create

```bash
hello.sh
```

Print

```
Welcome to Bioinformatics
```

---

## Exercise 2

Create a variable.

```bash
sample="SRR123456"
```

Print it.

---

## Exercise 3

Write a loop.

```bash
for i in 1 2 3 4 5
do
    echo $i
done
```

---

## Exercise 4

Create a function.

```bash
greet(){

echo "Hello"

}

greet
```

---

## Exercise 5

Write a script that prints all FASTQ filenames.

```bash
for sample in *.fastq.gz
do
    echo $sample
done
```

---

# ⚠️ Common Mistakes

> [!WARNING]
>
> - Forgetting the shebang (`#!/bin/bash`).
> - Not making the script executable with `chmod +x`.
> - Forgetting to quote variables such as `"$sample"` when filenames may contain spaces.
> - Hardcoding file paths instead of using variables.

---

# 🧠 Interview Corner

### ❓ What is a Bash script?

A Bash script is a file containing Linux commands that are executed automatically by the Bash shell.

---

### ❓ Why use Bash scripting in bioinformatics?

To automate repetitive tasks such as quality control, alignment, file management, and report generation.

---

### ❓ What does `#!/bin/bash` do?

It specifies that the script should be executed using the Bash interpreter.

---

### ❓ What does `$1` represent?

The first command-line argument passed to the script.

---

### ❓ Why are loops useful in NGS?

They allow the same analysis to be performed on many sequencing files automatically.

---

# 📝 Lesson Summary

- Bash scripts automate Linux commands.
- Variables store information.
- Loops process multiple files efficiently.
- Functions organize reusable code.
- Bash scripting is the foundation of automated bioinformatics pipelines.

---

# ⚡ Quick Revision

| Command | Purpose |
|---------|---------|
| `#!/bin/bash` | Bash interpreter |
| `chmod +x script.sh` | Make executable |
| `./script.sh` | Run script |
| `$1` | First argument |
| `for ... do ... done` | Loop |
| `if ... then ... fi` | Conditional |
| `function_name(){}` | Function |

---

# 📚 References

- GNU Bash Manual
- Ubuntu Documentation
- Bioinformatics Data Skills (Book)
- Advanced Bash-Scripting Guide

---

# ➡️ Next Lesson

**Conda & Mamba for Bioinformatics Environment Management**
