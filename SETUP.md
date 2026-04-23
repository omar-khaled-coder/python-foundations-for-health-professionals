# Setup Guide — Python Foundations for Health Professionals

**For:** newcomers to Python who want to work through this course. No prior programming experience assumed.
**Estimated time:** 60–90 minutes (including downloads)

---

## What you will set up

By the end of this guide, your laptop will have:

1. **Python 3.11+** — the programming language and its interpreter
2. **Git** — the tool that lets us share code
3. **Visual Studio Code (VSCode)** — your code editor
4. **Python and Jupyter extensions** for VSCode
5. **A GitHub account** — for accessing course materials
6. **A working "Hello" test file** — proof that everything runs

If you have no idea what any of this is, that's fine. You don't need to understand it now. Just follow the steps.

---

## A short note before you start

- **Read each step before you do it.** Don't skip.
- **Write down anything weird you see** — we might discuss it in class.
- **Take screenshots of error messages.** If something fails, a screenshot helps whoever is supporting you.
- **Close other apps** while installing, to avoid slowdowns.

---

## Part 1 — Install Python

Python is both a programming language and a program that runs on your computer. You need the program installed.

### On Windows

1. Go to **https://www.python.org/downloads/**
2. Click the yellow button **"Download Python 3.x.x"** (the latest version).
3. Run the installer.
4. **CRITICAL:** On the very first installer screen, **check the box that says `Add python.exe to PATH`** at the bottom. This is the single most common mistake. If you miss this, Python will be installed but your terminal won't find it.
5. Click **"Install Now"**. Wait 1–2 minutes.
6. When done, click "Close".

### On macOS

1. Go to **https://www.python.org/downloads/macos/**
2. Download the **macOS 64-bit universal2 installer** for the latest stable version.
3. Open the `.pkg` file and follow the installer.
4. Default settings are fine.

### Verify Python is installed

Open a terminal:
- **Windows:** Press `Win + R`, type `powershell`, press Enter.
- **macOS:** Press `Cmd + Space`, type `Terminal`, press Enter.

Type exactly:

```
python --version
```

Press Enter. You should see something like:

```
Python 3.12.2
```

If you see this — you're done with Part 1. If you see "command not found" or "python is not recognized":

- **Windows:** You probably forgot the `Add python.exe to PATH` checkbox. Uninstall Python from Settings → Apps, then reinstall. Pay attention to the checkbox this time.
- **macOS:** Try `python3 --version` instead. macOS uses `python3`. That's fine.

---

## Part 1.5 — Install Git

Git is the tool that lets us move code and data between your laptop and the cloud. We'll use it on day one.

### On Windows

1. Go to **https://git-scm.com/download/win** — download starts automatically.
2. Run the installer. **Accept all defaults** unless you know what you're doing.
3. One exception: on the screen "Choosing the default editor used by Git", select **"Use Visual Studio Code"** (if VSCode is already installed) or just leave the default. It doesn't matter for this course.

### On macOS

Easiest path — the system-provided version is fine for our needs:

1. Open **Terminal.app**.
2. Type:
   ```
   git --version
   ```
3. If Git is installed, you see a version number. If not, macOS will offer to install "Xcode Command Line Tools" automatically. Accept. Wait 5–10 minutes.

### Verify Git is installed

In your terminal, type:

```
git --version
```

You should see something like:

```
git version 2.43.0
```

If you do — done with Part 1.5.

---

## Part 2 — Install Visual Studio Code (VSCode)

VSCode is the editor we will write code in. It's free and made by Microsoft.

1. Go to **https://code.visualstudio.com/**
2. Click the big blue **"Download"** button. It auto-detects your OS.
3. Run the installer.
   - **Windows:** Accept the default options, but **check** the boxes that say *"Add to PATH"* and *"Register Code as an editor for supported file types"*.
   - **macOS:** Drag `Visual Studio Code.app` into the Applications folder.
4. Open VSCode.

You should see a window with a blue sidebar on the left and a "Welcome" tab.

---

## Part 3 — Install VSCode Extensions

Extensions add features to VSCode. We need two.

1. In VSCode, click the **Extensions icon** in the left sidebar. It looks like four squares, one separated. Or: press `Ctrl+Shift+X` (Windows) / `Cmd+Shift+X` (macOS).
2. In the search box, type `Python`.
3. Click the first result — the one by **Microsoft**, with millions of downloads. Click **"Install"**. Wait until it finishes.
4. In the search box, type `Jupyter`.
5. Click the first result — again by **Microsoft**. Click **"Install"**.

Both extensions are now installed. You don't need to configure anything.

---

## Part 4 — Create a GitHub account

GitHub is the world's most-used platform for sharing code. All course materials live on it. You need an account to access them.

1. Go to **https://github.com/signup**
2. Use an **email address you will keep access to** (your university mail is fine).
3. Choose a **username** you're comfortable with professionally. Your real name, a variation of it, or a short handle. This will be visible to instructors and peers.
4. Confirm the email GitHub sends you.
5. Skip all "Getting Started" prompts — we don't need anything special yet.

**Done.** Write down your username somewhere — you'll need it on the first day.

---

## Part 5 — Verify Google account

You probably already have one. If not:

1. Go to **https://accounts.google.com/signup**
2. Create an account — your university mail is fine.

You need this for **Google Colab**, which we'll use later in the course when we work with Machine Learning (we need free GPU access).

---

## Part 6 — The functional test: "Hello"

This proves that everything works together. It's the most important step.

### Step 6.1 — Create a folder for the course

Somewhere on your computer (e.g., your Documents folder), create a new folder called:

```
python_foundations
```

This is where all your course work will live. Keep it tidy.

### Step 6.2 — Open the folder in VSCode

1. In VSCode: **File → Open Folder…** (or on macOS: **File → Open…**)
2. Navigate to `python_foundations`, click **Open**.
3. You might see a pop-up asking "Do you trust the authors?" — click **Yes, I trust the authors**.

### Step 6.3 — Create your first Python file

1. In VSCode's left sidebar (the file explorer), hover over the folder name `python_foundations`.
2. Click the **New File** icon that appears (a small page with a plus sign).
3. Name the file exactly: `hello.py`
4. Press Enter.

A new tab opens with an empty file.


### Step 6.4 — Write the code

Type **exactly** this into the file:

```python
print("Hello, Python!")
```

Save the file: `Ctrl+S` (Windows) / `Cmd+S` (macOS).

### Step 6.5 — Run the file

Two ways:

**Option A — the easy way:** In the top-right corner of VSCode, click the little **triangle/play button** (▷). It says "Run Python File" when you hover over it.

**Option B — the terminal way (try this too, because it's what we'll use later):**
1. Open VSCode's integrated terminal: **Terminal → New Terminal** (top menu). A panel opens at the bottom.
2. Type:
   ```
   python hello.py
   ```
   (On macOS: `python3 hello.py`)
3. Press Enter.

### Step 6.6 — The expected output

In the terminal panel, you should see:

```
Hello, Python!
```

**If you see this: YOU ARE DONE.** Celebrate. Close the laptop. See you in class.

---

## If something went wrong

Below are the three most common problems.

### Problem A — "python is not recognized" or "command not found"

Python isn't on your system PATH. See end of Part 1. Reinstall Python with the PATH option checked.

### Problem B — VSCode says "Select Python Interpreter"

A yellow bar appears at the top of VSCode asking you to choose an interpreter.
1. Click it.
2. Choose the Python version you installed (usually the top option).
3. Try running `hello.py` again.

### Problem C — The file runs but nothing prints

Check that your file contains exactly:
```python
print("Hello, Python!")
```
Note: **lowercase `print`**, **round brackets**, **quotation marks around the text**, **exclamation mark**. One wrong character = no output.

---

## Still stuck?

Email the instructor with:

1. Your operating system (Windows 10/11, macOS version, Linux distro)
2. A **screenshot** of the error message
3. The **part and step number** where you got stuck (e.g., "Part 1, Step 4")

Replies typically come within 24 hours.

---

## For those who are ahead

If you finish the setup in 30 minutes and are bored, here are optional extras. Doing them gives you a head start. **They are voluntary.** Don't stress about them.

- **Install a few Python packages:** In the VSCode terminal, run:
  ```
  pip install numpy pandas matplotlib jupyter
  ```
  (On macOS: `pip3 install ...`)
- **Open a Jupyter notebook in VSCode:** Create a new file called `scratch.ipynb`. VSCode will open it as a notebook. Create a code cell, type `1 + 1`, and press `Shift+Enter`. You should see `2`.
- **Explore GitHub:** Find one repository related to health data. Star it.
- **Watch:** the first 10 minutes of Corey Schafer's "Python Tutorial for Beginners" on YouTube. Gentle primer on what we'll start with.

---

## See you in the first session

Bring your laptop, your power cable, and a notebook for handwriting.
