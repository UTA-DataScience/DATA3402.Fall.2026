# DATA 3402 — Python for Data Science 2

**Fall 2026 · University of Texas at Arlington · Instructor: Amir Farbin**

Course materials are distributed through this repository. Pull regularly — lectures
and labs are pushed as the semester progresses.

## Updated files

**November 9:** `Lectures/Lecture.20/Lecture.20.ipynb` again: a stray Jupyter error message stored in one
cell's output (the top-correlations cell) was removed; nothing else changed. If you have run or edited
your copy, set it aside before you pull, as below.

**October 28:** `Lectures/Lecture.20/Lecture.20.ipynb`, `Lectures/Lecture.21/Lecture.21.ipynb` and
`Kaggle Tabular Data.ipynb` were updated with more explanation (no code changed). If you have run or
edited your own copy of any of them, set it aside **before** you pull, or `git pull` will refuse or
conflict, and a conflicted notebook won't open in Jupyter:

```bash
mv Lectures/Lecture.20/Lecture.20.ipynb Lectures/Lecture.20/Lecture.20.mine.ipynb   # same for the others
git checkout -- Lectures/Lecture.20/Lecture.20.ipynb     # only if git still sees it as modified
git pull
```

If you never touched them, just `git pull`.

## Contents

| Path | What's there |
|------|--------------|
| `syllabus.pdf` | Course syllabus, grading breakdown, policies |
| `Chapters/` | The course text, one PDF per chapter, with a review question set |
| `Lectures/` | One folder per lecture: notebooks and/or slide PDFs |
| `Labs/` | One folder per lab assignment, plus the GitHub setup guide |
| `sample.ipynb` | Notebook whose one code cell prints `Hello World!`, to check Jupyter can run code |
| `requirements.txt` | Python packages used in the course |

## The course text

`Chapters/` holds the written version of the material — the same ground the lectures cover, but
in prose you can read at your own pace and go back to. Start with the chapter, use the lecture
slides as the map, and use the review questions to find out what didn't stick.

| File | Covers |
|---|---|
| `Chapter.01.Computers.pdf` | How computers work, from a transistor to an iPhone. Lecture 2 + Lab 1. |
| `Chapter.01.Review.Questions.pdf` | 100 multiple-choice questions on Chapter 1, tagged easy / medium / hard. |
| `Chapter.03.Probability.and.Statistics.pdf` | Probability, Bayes, distributions, and generating data from them. Lectures 6 and 7. |

The questions are for self-testing and are not graded. In most of them at least one wrong option
is what you would believe if you *almost* understood the idea, so read them carefully.

Chapter 3 pairs with a notebook: read the chapter for the reasoning, then work through
`Lectures/Lecture.7/Lecture.7.ipynb`, which turns it into code — a random number generator built
from scratch, a histogram function written by hand, accept/reject sampling and Monte Carlo
integration. Lab 3 draws directly on it.

More chapters land as the semester goes on.

## Getting started

We did all of this together in the first lab session. These are the same steps, so you
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

4. **Clone this repository and install the requirements.** The clone is read-only;
   `git pull` brings you new lectures and labs as they are released. Submitting work also
   needs your own fork — see *Labs and submission* below.

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
Kaggle competition data, image sets). They are not in this repository: you download
them when a lecture or lab tells you to. `.gitignore` excludes them under the names the
course uses, along with the pickles and model files the notebooks write — don't commit
them. GitHub refuses files over 100 MB, so a committed dataset stops your pushes.

## Labs and submission

**Lab 5 has two parts.** `Labs/Lab.5/Lab.5.ipynb` is the matrix class, the main assignment.
`Labs/Lab.5/Lab.5.CommandLine.ipynb` is the shorter piece we work through in the lab session:
getting a data file into shape from the command line, using `bank-churn.csv` beside it and
files already in `Lectures/`. Nothing to download.

Lab work is submitted through your own **fork** of this repository:

- you fork this repository once on GitHub, giving you your own copy under your account;
- you **pull from this repository** to receive new lectures and labs as they are released;
- you do your lab work in your fork and **push to your fork**, which is where it is graded.

We set this up together in the Lab 4 session (Friday 9/11). If you missed it or need to
start over, Part 1 of `Labs/Lab.4/Lab.4.ipynb` walks through it, and `Labs/GitHub-Setup.pdf`
has the same steps line by line — including logging in to GitHub from the terminal, which
you need before your first push — plus a table of what to do when git complains. In short:

1. **Fork this repository.** On its GitHub page, press **Fork** at the top right and fork it
   into your own account.

2. **Clone your fork**, not this repository:

   ```bash
   cd ~/Data-3402
   git clone https://github.com/YOUR_USERNAME/DATA3402.Fall.2026.git
   cd DATA3402.Fall.2026
   ```

   **Already have the clone from *Getting started*?** Then `~/Data-3402/DATA3402.Fall.2026`
   exists, and cloning your fork into the same place stops with *destination path already
   exists*. Don't clone again, and don't delete that folder: `cd ~/Data-3402/DATA3402.Fall.2026`
   and carry on with step 3, which works on that clone unchanged.

3. **Fix the remotes**, so that pulls come from this repository and pushes go to your fork:

   ```bash
   git remote remove origin
   git remote add origin https://github.com/UTA-DataScience/DATA3402.Fall.2026.git
   git remote set-url --push origin https://github.com/YOUR_USERNAME/DATA3402.Fall.2026.git
   git remote -v
   ```

   `git remote -v` should show this repository for **fetch** and your fork for **push**. If
   both lines show the same URL, the `set-url --push` didn't take; run it again. If you use SSH
   keys, your fork's URL is `git@github.com:YOUR_USERNAME/DATA3402.Fall.2026.git`, in both the
   clone and the `set-url --push`.

From then on `git pull` brings class material and `git push` sends your work to your fork.

**The moment you pull a new lab, copy it to a new name and work only in the copy** — never
edit the file we handed out:

```bash
cp Labs/Lab.3/Lab.3.ipynb Labs/Lab.3/Lab.3.solution.ipynb
```

`git pull` only touches files it recognizes from this repository, so a copy under a name we
never handed out can't conflict with a fix we push later. To submit, commit your copy, push,
and check on GitHub that your fork shows the new commit:

```bash
git add Labs/Lab.3/Lab.3.solution.ipynb
git commit -m "Lab 3 submission"
git push
```

Commit only your own copies. If you run a lecture notebook in place and commit it, the next
release of that lecture can conflict when you pull; `Labs/GitHub-Setup.pdf` says how to recover.

## Communication

All course communication goes through Teams — not email.
