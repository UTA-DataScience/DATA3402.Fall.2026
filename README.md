# DATA 3402 — Python for Data Science 2

**Fall 2026 · University of Texas at Arlington · Instructor: Amir Farbin**

Course materials are distributed through this repository. Pull regularly — lectures
and labs are pushed as the semester progresses.

## Contents

| Path | What's there |
|------|--------------|
| `syllabus.pdf` | Course syllabus, grading breakdown, policies |
| `Chapters/` | The course text, one PDF per chapter, with a review question set |
| `Lectures/` | One folder per lecture: notebooks and/or slide PDFs |
| `Labs/` | One folder per lab assignment, plus the GitHub setup guide |
| `sample.ipynb` | Minimal notebook to check your environment works |
| `requirements.txt` | Python packages used in the course |

## The course text

`Chapters/` holds the written version of the material — the same ground the lectures cover, but
in prose you can read at your own pace and go back to. Start with the chapter, use the lecture
slides as the map, and use the review questions to find out what didn't stick.

| File | Covers |
|---|---|
| `Chapter.01.Computers.pdf` | How computers work, from a transistor to an iPhone. Lecture 2 + Lab 1. |
| `Chapter.01.Review.Questions.pdf` | 100 multiple-choice questions on Chapter 1, tagged easy / medium / hard. |

The questions are for self-testing and are not graded. In most of them at least one wrong option
is what you would believe if you *almost* understood the idea, so read them carefully.

More chapters land as the semester goes on.

## Getting started

We do all of this together in the first lab session. These are the same steps, so you
can catch up or start over.

You need Linux, macOS, or Windows **with WSL**. On Windows, WSL is required — not a
suggestion. Google Colab is an acceptable fallback if your machine can't handle the
later assignments, but it is not a substitute for having a working setup.

1. **Get a Unix shell.**
   - *Windows:* in PowerShell **as Administrator**, run `wsl --install`, then reboot.
     Launch **Ubuntu** from the Start menu and set a username and password when it
     asks. Write the password down — every `sudo` needs it.
   - *macOS:* open Terminal and run `xcode-select --install`.
   - *Linux:* you already have one.

2. **Install the system packages.** On Ubuntu/WSL/Debian:

   ```bash
   sudo apt update
   sudo apt install python3 python3-pip python3-venv git
   ```

   On macOS these came with the command line tools. Then close and reopen the terminal.

3. **Make a course directory with its own virtual environment.**

   ```bash
   cd ~
   mkdir -p Data-3402
   cd Data-3402
   python3 -m venv .venv
   source .venv/bin/activate
   ```

   Your prompt should now start with `(.venv)`. That is a private Python for this
   course — nothing you install into it can break your system. **Run the `source` line
   again in every new terminal**; most "module not found" problems are just a forgotten
   activation.

   Do not use `sudo pip install`. Current Ubuntu blocks it with
   `externally-managed-environment`, on purpose; the virtual environment is the fix.

   **Windows:** keep all of this in your Linux home directory (`~`), *not* under
   `/mnt/c`. Git and Jupyter are slow and unreliable across that boundary. Your Windows
   drives are visible from Linux at `/mnt/c`, and your Linux files are visible from
   Windows File Explorer at `\\wsl.localhost\Ubuntu`.

4. **Clone this repository and install the requirements.** The clone is read-only for
   now; `git pull` brings you new lectures and labs as they are released.

   ```bash
   cd ~/Data-3402
   git clone https://github.com/UTA-DataScience/DATA3402.Fall.2026.git
   cd DATA3402.Fall.2026
   pip install -r requirements.txt
   ```

   No `sudo` on that last line — inside the virtual environment you are already allowed.

5. **Check that it works.**

   ```bash
   python3 -c "import numpy, pandas, matplotlib; print('ok')"
   jupyter lab
   ```

   Open `sample.ipynb`, click the code cell, and press **Shift+Enter**. `Ctrl-C` twice
   in the terminal stops Jupyter.

   Every time you come back: `cd ~/Data-3402 && source .venv/bin/activate`, then
   `cd DATA3402.Fall.2026`.

## Notes on large data

Several lectures and labs use datasets too large to keep in git (the SUSY dataset,
Kaggle competition data, image sets). Those are downloaded by the notebooks
themselves and are excluded via `.gitignore` — don't commit them.

## Labs and submission

Lab work is submitted through your own **fork** of this repository:

- you fork this repository once on GitHub, giving you your own copy under your account;
- you **pull from this repository** to receive new lectures and labs as they are released;
- you do your lab work in your fork and **push to your fork**, which is where it is graded.

**Don't fork yet.** The clone from *Getting started* is all you need to follow along, and
it is deliberately read-only — you can pull, but you can't push to it. We set up forks
together, step by step, in the lab session that covers git and GitHub, and that session
reuses the directory you already have: the existing remote is renamed to `upstream` and
your fork becomes `origin`. Nothing you do today has to be undone.

`Labs/Git Hub Setup Guide (wsl & Mac Os).pdf` is the written version of that session.
Read it then, not now — and note that it still shows a previous semester's repository
name in its example URLs.

## Communication

All course communication goes through Teams — not email.
