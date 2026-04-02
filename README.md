# GIT AND GTIHUB

1. Basics
2. Basic commands
3. Pull, merging, branching, strateging for Devops
4. Hooks
5. Repo setup end to end (GitHub Actions/ CI/CD)
6. Certificate of Workshop

- GIT - Version Control System

- GitHub vs GitLab vs Bitbucket  ->are platforms and  all uses git at the background.
	- CI/CD
- VCS - have an otion to revocer file, not in the File sstem

Untracked 	Staged 		Tracked

- git init
- git status
- git add
- git commit -m "test"
- git restore <file>


- Create a Repo in GitHub


Settings -> Developer Settings -> PAT(PHysical Access Tokens) 
	- which helps is push from local to GitHub, where the fatal error etc wont happen.

- FORK - is the copy of the repository - GitHub to github
- Clone - "   GitHub to local
- git push and git pull

# ------------- Branches --------------
- Branching Strategy
by default branch is master in local
by default branch is main in GitHub

- git branch
- git checkout -b dev  or git branch dev
- git switch dev
Every branch in git maintains its own copy

- Feature branch
- HEAD -> represents your latest commit 
	- git log

- git fetch // bring branches from the remote to local
- git pull // to bring the branch specific changes to local

-----
git pull origin master --rebase


# ------------- Git Hooks --------------
- can create 

cd .git
.git / ls
	hooks
cd hooks
ls
	// you can see list of pre-commit-sample ec samples

pip install flake8  // tool used to test the code-quality test


// pre commit shell script from gemini:

#!/bin/bash

# Get a list of all staged Python files (.py)
STAGED_FILES=$(git diff --cached --name-only --diff-filter=ACM | grep ".py$")

# If no Python files are staged, exit early
if [ -z "$STAGED_FILES" ]; then
    exit 0
fi

echo "--- Running Flake8 Quality Check ---"

# Run flake8 on the staged files
# We use --count to get the total number of errors
flake8 $STAGED_FILES

# Capture the exit code of the last command
RESULT=$?

if [ $RESULT -ne 0 ]; then
    echo ""
    echo "❌ ERROR: Flake8 found issues in your code."
    echo "Please fix the errors above before committing."
    echo "----------------------------------------"
    exit 1
fi

echo "✅ Quality check passed. Proceeding with commit..."
exit 0


# -----------GITHUB ACTIONS = DEPLOYMENT ------------

GitHub ACTIONS - in-built toolsimilar to Jenkins

/.GitHub/workflow

- Integrate AWS and GitHub Actions
