# FPC-Module-SCSE1013
Fundamental Programming Concept

# FPC Module: Getting Started with GitHub

## What is GitHub?

GitHub is an online platform for storing, sharing and working together on code. It is built on Git, a version control system that records every change made to a project, so you can see who changed what and go back to any earlier version. More than 100 million developers use it, from students to companies such as Microsoft and Google.

**What GitHub is used for:**

- **Backup and access anywhere.** Your code is stored online, so it is safe if your laptop breaks and you can work on it from any computer.
- **Version history.** Every change is recorded, so mistakes can be undone and progress can be tracked.
- **Collaboration.** Several people can work on the same project at the same time without overwriting each other's work.
- **Code review.** Teammates can comment on and approve changes before they are merged, through pull requests.
- **Assignment submission.** Lecturers can receive and check work through a repository link and see its full history.
- **Portfolio.** Your public repositories show employers what you can build, like an online CV for programmers.
- **Open source.** Anyone can explore, learn from and contribute to millions of public projects.

## Module overview

By the end of this module, every FPC student can store their code on GitHub, track changes with Git, and submit work through a repository. No prior Git experience is assumed.

**Learning outcomes.** After completing this module, students will be able to:

1. Explain the difference between Git and GitHub, and the purpose of version control.
2. Set up a GitHub account and install and configure Git on their own computer.
3. Create, clone and update a repository using the core commands: `clone`, `add`, `commit`, `push`, `pull`.
4. Use branches and pull requests to work safely and collaborate in a group.
5. Resolve a simple merge conflict.

**Prerequisites.** A laptop (Windows, macOS or Linux), an internet connection, and a student email address. Basic familiarity with opening a terminal or command prompt helps but is not required.

## Part 1: Concepts

Git is a tool on your computer that records snapshots of your code; GitHub is a website that stores those snapshots online so you can back them up, share them and collaborate.

**Why version control?** Without it, students end up with folders like `assignment_final`, `assignment_final2` and `assignment_REALLY_final`. With Git, every saved version is kept in one folder with a message explaining what changed, and you can go back to any earlier version.

**Analogy.** Think of Git as a save system in a video game: each commit is a save point. GitHub is the cloud save, so your progress survives even if your laptop does not.

**Key terms.**

| Term | Meaning | Example |
| --- | --- | --- |
| Repository (repo) | A project folder tracked by Git, including its full history | `fpc-lab1` |
| Commit | A saved snapshot of changes, with a message | "Add input validation to calculator" |
| Staging area | The list of changes you have chosen to include in the next commit | Files added with `git add` |
| Local repo | The copy on your computer | `C:\Users\ali\fpc-lab1` |
| Remote repo | The copy on GitHub, usually named `origin` | `github.com/ali/fpc-lab1` |
| Clone | Download a remote repo to your computer for the first time | `git clone <url>` |
| Push | Upload your local commits to GitHub | `git push` |
| Pull | Download new commits from GitHub to your computer | `git pull` |
| Branch | A separate line of work, so changes do not affect the main code until ready | `feature-login` |
| Merge | Combine the changes from one branch into another | Merge `feature-login` into `main` |
| Pull request (PR) | A request on GitHub to review and merge a branch | "Add login menu" PR |
| Merge conflict | Git cannot combine two changes to the same lines automatically | Two members edited line 12 |

**The basic cycle** students will repeat for every piece of work:

1. **Edit** files in your code editor.
2. **Stage** the changes you want to save: `git add`.
3. **Commit** them with a clear message: `git commit -m "..."`.
4. **Push** to GitHub: `git push`.
5. Before starting work next time, **pull** the latest changes: `git pull`.

## Part 2: Setup

Setup is done once per computer; students should finish it before the first hands-on lab.

### Step 1: Create a GitHub account

1. Go to [github.com](https://github.com) and click **Sign up**.
2. Use your student email so you can apply for student benefits later.
3. Choose a professional username (for example `aliahmad-dev`, not `xX_gamer_Xx`). Recruiters may see it.
4. Verify your email address.
5. Turn on two-factor authentication under **Settings → Password and authentication**. GitHub requires it for most accounts that contribute code.

**Optional: GitHub Student Developer Pack.** Apply at [education.github.com](https://education.github.com) with your student email and proof of enrolment to get GitHub Pro and free developer tools while you study.

### Step 2: Install Git

| OS | How to install | Notes |
| --- | --- | --- |
| Windows | Download from [git-scm.com](https://git-scm.com/downloads) and run the installer | Default options are fine. Installs **Git Bash** and Git Credential Manager. |
| macOS | Run `git --version` in Terminal; accept the prompt to install Command Line Tools | Or install with Homebrew: `brew install git` |
| Linux (Ubuntu/Debian) | `sudo apt update && sudo apt install git` | Use your distro's package manager otherwise |

Check it worked by opening a terminal (Git Bash on Windows) and running:

```bash
git --version
```

Any version number in the output means Git is installed.

### Step 3: Tell Git who you are

Git stamps every commit with your name and email. Use the **same email as your GitHub account** so commits link to your profile.

```bash
git config --global user.name "Your Name"
git config --global user.email "Your Email"
git config --global init.defaultBranch main
git config --list
```

The last command shows your settings so you can confirm them.

### Step 4: Connect your computer to GitHub (authentication)

GitHub no longer accepts your account password for `git push`. Pick one of these methods.

- **Option A, browser sign-in (recommended for beginners).** On Windows, Git Credential Manager pops up a browser login on your first push; sign in once and it is remembered. On any OS, you can instead install [GitHub CLI](https://cli.github.com) and run `gh auth login`, then follow the prompts (choose GitHub.com, HTTPS, and log in with a web browser).
- **Option B, SSH key.** Generate a key and add the public half to GitHub:

```bash
ssh-keygen -t ed25519 -C "Your Eamil"
cat ~/.ssh/id_ed25519.pub
```

Copy the printed line into **GitHub → Settings → SSH and GPG keys → New SSH key**, then test with `ssh -T git@github.com`. When cloning, use the SSH URL (`git@github.com:...`) instead of the HTTPS one.

### Step 5 (optional): Friendlier tools

- **VS Code** has Git built in: the Source Control panel lets you stage, commit and push with buttons. Students should still learn the commands first.
- **GitHub Desktop** ([desktop.github.com](https://desktop.github.com)) is a graphical app that suits students who struggle with the terminal.

**Setup checkpoint:** `git --version` works, `git config --list` shows your name and email, and you can sign in to GitHub from your computer.

## Part 3: Your first repository

In this guided lab, each student creates a repo on GitHub, clones it, adds a program, and pushes it back, completing the full basic cycle once.

### 3.1 Create a repository on GitHub

1. Click **+ → New repository** (top right of GitHub).
2. Name it `fpc-lab1`.
3. Set visibility to **Private** for graded work, unless your lecturer says otherwise.
4. Tick **Add a README file**.
5. Under **Add .gitignore**, pick the template for your course language (for example **C** or **Python**).
6. Click **Create repository**.

### 3.2 Clone it to your computer

On the repo page, click the green **Code** button and copy the HTTPS URL (or SSH URL if you set up SSH). Then:

```bash
cd Documents
git clone https://github.com/<your-username>/fpc-lab1.git
cd fpc-lab1
ls
```

You should see `README.md`. This folder is now a local repo linked to GitHub.

### 3.3 Add a file and check status

Create a small program in the folder, for example `hello.c` (or `hello.py`), using your editor. Then ask Git what changed:

```bash
git status
```

Git lists `hello.c` as **untracked**: it sees the file but is not saving it yet.

### 3.4 Stage and commit

```bash
git add hello.c
git status
git commit -m "Add hello world program"
```

After `git add`, the file shows under **Changes to be committed**. After `git commit`, the snapshot is saved locally. Use `git add .` to stage every changed file in the folder.

**Writing good commit messages.** Describe what the change does, in a short imperative phrase.

| Good | Bad |
| --- | --- |
| Add menu loop to calculator | update |
| Fix division by zero in average function | asdf |
| Rename variables for readability | final version!!! |

### 3.5 Push to GitHub

```bash
git push
```

The first push may open a browser sign-in (Part 2, Step 4). Refresh the repo page on GitHub: `hello.c` and your commit message now appear.

### 3.6 Edit the README on GitHub, then pull

This simulates a change made somewhere else (another computer or a teammate).

1. On GitHub, open `README.md`, click the pencil icon, add a line such as your name and matric number, and click **Commit changes**.
2. On your computer, run:

```bash
git pull
```

Open `README.md` locally: the new line is there. **Habit to build: always `git pull` before you start working.**

### 3.7 View history

```bash
git log --oneline
```

Each line is one commit, newest first. On GitHub, click **Commits** on the repo page to see the same history.

### 3.8 What .gitignore is for

The `.gitignore` file lists files Git should never track, such as compiled programs and editor settings. A typical entry list for a C course:

```
*.exe
*.o
a.out
.vscode/
```

Commit source code, not the files your compiler produces.

## Part 4: Branches, pull requests and collaboration

Group members should never all edit `main` directly; each person works on their own branch and merges through a pull request, which keeps `main` working and shows who did what.

### 4.1 Create and switch branches

```bash
git switch -c feature-menu      # create a new branch and move to it
git branch                      # list branches; * marks the current one
git switch main                 # go back to main
```

Commits made on `feature-menu` do not touch `main` until you merge them.

### 4.2 Push a branch and open a pull request

```bash
git switch feature-menu
# edit files...
git add .
git commit -m "Add main menu with three options"
git push -u origin feature-menu
```

The `-u` links your local branch to GitHub, so later you can just type `git push`. Then on GitHub:

1. Click **Compare & pull request** (it appears after the push), or go to **Pull requests → New pull request**.
2. Set **base** to `main` and **compare** to `feature-menu`.
3. Write a title and a short description of what changed and how to test it.
4. Add a teammate as **Reviewer**.
5. After review, click **Merge pull request**, then **Delete branch**.
6. Locally, update `main`: `git switch main` then `git pull`.

### 4.3 Group assignment workflow

1. **One member** creates the repo and adds the others under **Settings → Collaborators**.
2. **Each member** clones the repo.
3. Before each task: `git switch main` and `git pull`.
4. Create a branch named after the task: `git switch -c <name>-<task>`, for example `siti-file-io`.
5. Commit small, logical changes often.
6. Push the branch and open a pull request.
7. Another member reviews and merges it.
8. Everyone pulls `main` again before the next task.

Tip: agree on who owns which files or functions. Fewer people editing the same lines means fewer conflicts.

### 4.4 Resolving a merge conflict

A conflict happens when two branches change the **same lines** of the same file. Git stops and marks the file like this:

```
<<<<<<< HEAD
printf("Welcome to the calculator\n");
=======
printf("Welcome to FPC Calculator v2\n");
>>>>>>> feature-menu
```

The part above `=======` is your current branch; the part below is the incoming branch. To fix it:

1. Open the file and decide what the final code should be (keep one side, the other, or combine them).
2. Delete the markers `<<<<<<<`, `=======` and `>>>>>>>`.
3. Save, then mark it resolved and commit:

```bash
git add main.c
git commit -m "Resolve conflict in welcome message"
git push
```

VS Code highlights conflicts and offers **Accept Current / Accept Incoming / Accept Both** buttons, which helps beginners. GitHub can also resolve simple conflicts in the browser from the pull request page.

## Part 5: Lab exercises

Students complete three exercises, individually first and then in pairs, and submit their repository links for checking.

### Exercise 1: Personal repo (individual)

1. Create a private repo named `fpc-<matric-number>` with a README and a `.gitignore`.
2. Clone it, add a working program from a previous FPC lab, and push it.
3. Edit the README to include your name, matric number and a one-line description of the program.
4. Make **at least three commits** with meaningful messages.

### Exercise 2: Branch and pull request (individual)

1. Create a branch `improve-input`.
2. Add input validation to your program (for example, reject negative numbers).
3. Push the branch, open a pull request into `main`, and merge it yourself.
4. Pull `main` locally and confirm the change is there.

### Exercise 3: Pair collaboration and conflict (pairs)

1. Student A creates repo `fpc-pair-<A>-<B>` and adds Student B as a collaborator.
2. Both clone it. Each creates their own branch and edits **the same line** of `README.md`.
3. A opens a PR and merges it. B opens a PR, which now has a conflict.
4. B resolves the conflict (in VS Code or on GitHub) and merges.

### Submission checklist

- [ ] Repo link submitted via the course LMS
- [ ] README has name, matric number and program description
- [ ] At least 3 commits with meaningful messages
- [ ] One merged pull request from `improve-input`
- [ ] No compiled files (`.exe`, `.o`, `a.out`) committed
- [ ] Pair repo shows a resolved merge conflict in its history

### Suggested marking rubric (10 marks)

| Criterion | Marks |
| --- | --- |
| Repo set up correctly (README, .gitignore, private) | 2 |
| Commit history: at least 3 commits, clear messages | 3 |
| Branch and pull request merged correctly | 2 |
| Merge conflict resolved, code still runs | 2 |
| No unnecessary files committed | 1 |

## Quick reference

### Command cheat sheet

| Command | What it does |
| --- | --- |
| `git clone <url>` | Download a repo from GitHub |
| `git status` | Show changed, staged and untracked files |
| `git add <file>` / `git add .` | Stage one file / all changes |
| `git commit -m "msg"` | Save staged changes as a commit |
| `git push` | Upload commits to GitHub |
| `git pull` | Download and merge new commits from GitHub |
| `git log --oneline` | Show commit history, one line each |
| `git diff` | Show unstaged changes line by line |
| `git switch -c <branch>` | Create a branch and switch to it |
| `git switch <branch>` | Switch to an existing branch |
| `git branch` | List local branches |
| `git restore <file>` | Discard uncommitted changes to a file |
| `git push -u origin <branch>` | Push a new branch to GitHub the first time |

### GitHub Video Tutorial

[![Watch the tutorial](https://markdown-videos-api.jorgenkh.no/youtube/ATVkjDNhQzU)](https://www.youtube.com/watch?v=ATVkjDNhQzU)


### Common errors and fixes

| Error message (shortened) | Cause | Fix |
| --- | --- | --- |
| `fatal: not a git repository` | You are in the wrong folder | `cd` into the repo folder (it contains a hidden `.git` folder) |
| `Author identity unknown` | Name and email not configured | Run the `git config --global` commands in Part 2, Step 3 |
| `Support for password authentication was removed` | Used GitHub password to push | Use browser sign-in, `gh auth login`, or SSH (Part 2, Step 4) |
| `! [rejected] ... (fetch first)` | GitHub has commits you do not have | `git pull`, resolve any conflict, then `git push` |
| `CONFLICT (content): Merge conflict in ...` | Same lines changed on two branches | Follow Part 4.4 |
| `Permission denied (publickey)` | SSH key not added to GitHub | Add the public key in Settings, or clone with HTTPS instead |
| `src refspec main does not match any` | No commits yet, or branch is named `master` | Commit first; check the name with `git branch` |
| Editor opens with strange text after `git commit` | Forgot `-m` | Type a message, save and close; or in Vim press `Esc`, type `:wq`, press Enter |

### Good practices

- Pull before you start; push when you finish a session.
- Commit small, working changes with clear messages.
- Never commit passwords, API keys or personal data. Once pushed, assume it is public.
- Keep graded work in **private** repos to avoid plagiarism issues.
- Use branches and pull requests for group work; keep `main` runnable.

### References
- [GitHub Docs: Get started](https://docs.github.com/en/get-started)

