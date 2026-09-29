# Git Merge Conflict Demonstration

## Project Overview

This project demonstrates how Git handles a merge conflict when two feature branches modify the same line of the same file in different ways.

The project uses a simple Python Student Learning Portal.

Two feature branches were created from the same `main` commit:

* `feature-login-message`
* `feature-dashboard-message`

Both branches modified the same line in `app.py`.

---

## Branch Workflow

```text
main
│
├── feature-login-message
│
└── feature-dashboard-message
```

The workflow was:

1. Create the initial project on `main`.
2. Create `feature-login-message`.
3. Modify a specific line in `app.py`.
4. Commit and push the first branch.
5. Return to the original `main`.
6. Create `feature-dashboard-message` from the same base.
7. Modify the exact same line differently.
8. Commit and push the second branch.
9. Merge `feature-login-message` into `main`.
10. Attempt to merge `feature-dashboard-message`.
11. Git produces a merge conflict.
12. Inspect Git's conflict markers.
13. Manually resolve the conflict.
14. Test the resolved code.
15. Stage the resolved file.
16. Commit the conflict resolution.
17. Push the final merged history to GitHub.

---

## Conflict

The original line was:

```python
print("Welcome to the Student Learning Portal")
```

The login branch changed it to:

```python
print("Welcome to the Student Login Portal")
```

The dashboard branch changed the same line to:

```python
print("Welcome to the Student Dashboard")
```

Because both branches changed the same line differently, Git could not automatically determine which version should be used.

---

## Git Conflict Markers

During the conflict, Git inserted markers similar to:

```python
<<<<<<< HEAD
print("Welcome to the Student Login Portal")
=======
print("Welcome to the Student Dashboard")
>>>>>>> feature-dashboard-message
```

### Meaning

`<<<<<<< HEAD`

Marks the version currently checked out on `main`.

`=======`

Separates the two conflicting versions.

`>>>>>>> feature-dashboard-message`

Marks the version coming from the branch being merged.

---

## Conflict Resolution

The conflict was resolved manually by replacing the conflicting versions with a neutral application-level message:

```python
print("Welcome to the Student Learning Portal")
```

The conflict markers were then removed.

The application was tested before committing the resolution.

---

## Git Commands Used

### Initialize Git

```bash
git init
```

### Create branches

```bash
git switch -c feature-login-message
git switch main
git switch -c feature-dashboard-message
```

### Commit changes

```bash
git add .
git commit -m "Update message for login feature"
```

```bash
git add .
git commit -m "Update message for dashboard feature"
```

### Push branches

```bash
git push -u origin feature-login-message
git push -u origin feature-dashboard-message
```

### Merge first branch

```bash
git switch main
git merge feature-login-message
```

### Attempt second merge

```bash
git merge feature-dashboard-message
```

This produces the merge conflict.

### Check conflict

```bash
git status
```

### Resolve

Edit `app.py`, remove the conflict markers, and select the desired final code.

### Mark resolution

```bash
git add app.py
```

### Commit resolution

```bash
git commit -m "Resolve merge conflict between login and dashboard"
```

### Push final result

```bash
git push origin main
```

---

## Final Git History

The history can be viewed using:

```bash
git log --oneline --graph --decorate --all
```

This shows the separate feature branches, their commits, the merge, and the conflict-resolution commit.

---

## Running the Application

Run:

```bash
python app.py
```

Expected output:

```text
Welcome to the Student Learning Portal
```

---

## Repository

GitHub repository:

https://github.com/shanukashyap/Git-Merge-Conflict-Demonstration

---

## YouTube Demonstration


1. Initial project creation
2. Git repository initialization
3. Creation of the first feature branch
4. Modification of the target line
5. Commit and push
6. Creation of the second feature branch from the same base
7. Different modification to the same line
8. Commit and push
9. Merge of the first branch
10. Attempted merge of the second branch
11. Git merge conflict
12. Git conflict markers
13. Explanation of the conflicting versions
14. Manual conflict resolution
15. Testing the resolved application
16. Staging and committing the resolution
17. Pushing the final history
18. Final GitHub repository
19. Final Git history
20. Clean working tree
