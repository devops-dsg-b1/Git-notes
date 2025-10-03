## 1. You committed changes to the wrong branch. How do you fix it?
```bash
git checkout correct-branch
git cherry-pick <commit-hash>
git checkout wrong-branch
git reset --hard HEAD~1
````

---

## 2. You pushed sensitive data (like password) to remote. How do you remove it?

```bash
git filter-repo --invert-paths --path secrets.txt
git push origin --force
```

---

## 3. You made 5 commits in a feature branch, but manager wants them in a single commit before merge.

```bash
git rebase -i HEAD~5
# pick first commit, squash others
```

---

## 4. Your teammate force-pushed and your local branch is out of sync. How do you fix it?

```bash
git fetch origin
git reset --hard origin/main
```

---

## 5. You want to undo a commit that is already pushed but without rewriting history.

```bash
git revert <commit-hash>
git push origin main
```

---

## 6. You created changes but forgot to create a new branch, how do you move them?

```bash
git checkout -b new-feature
```

---

## 7. How do you see what changed in the last commit?

```bash
git show HEAD
```

---

## 8. How do you see which files are not tracked by Git?

```bash
git status
```

---

## 9. Your branch has 50 commits, but you only want to merge the last 2 commits into `main`.

```bash
git checkout main
git cherry-pick <commit1> <commit2>
```

---

## 10. You staged files accidentally, how do you unstage them?

```bash
git reset file1.txt
```

---

## 11. You want to delete a commit from history (local only).

```bash
git reset --hard HEAD~1
```

---

## 12. You deleted a branch accidentally. How do you recover it?

```bash
git reflog
git checkout -b branch-name <commit-hash>
```

---

## 13. You want to keep only some files from a commit.

```bash
git restore --source=HEAD~1 file1.txt
```

---

## 14. How do you see who changed a line in a file?

```bash
git blame app.py
```

---

## 15. Your repo is very big. How do you clone only one branch?

```bash
git clone -b feature --single-branch <repo-url>
```

---

## 16. You committed a large file by mistake and now `git push` is failing. How do you fix it?

```bash
git rm --cached largefile.zip
git commit -m "remove file"
git push
```

---

## 17. You want to apply changes from another branch without merging the full branch.

```bash
git cherry-pick <commit-hash>
```

---

## 18. You want to stash only one file, not all changes.

```bash
git stash push file1.txt
git stash pop
```

---

## 19. You want to compare your local branch with remote branch.

```bash
git fetch origin
git diff main origin/main
```

---

## 20. You want to rename a branch (local + remote).

```bash
git branch -m old-name new-name
git push origin :old-name
git push origin new-name
git branch -u origin/new-name
```

---

# ✅ Quick Summary

* Wrong branch? → `cherry-pick` + `reset`
* Remove pushed commit? → `revert`
* Combine commits? → `squash (rebase -i)`
* Accidentally deleted branch? → `reflog`
* Undo staged files? → `git reset`
* See who changed a line? → `git blame`
* Stash specific file? → `git stash push file.txt`
* Partial merge? → `git cherry-pick`
