# Git: Remove Latest Commit (Keep Changes), Pull Latest Code, and Push Again

If your push was rejected and you **don't want to lose your changes**, do **not** use `git reset --hard`.

Use the following steps:

```bash
git reset --soft HEAD~1
git stash
git pull origin main
git stash pop
git add .
git commit -m "Your latest changes"
git push -u origin main
```



# Git: Merge Branch Code

```bash
# 1. Check your current status
git status

# 2. Switch to prod
git checkout prod

# 3. Get the latest prod from GitHub
git pull origin prod

# 4. Merge dev into prod
git merge dev

# 5. :wq

# 6. Push the merged prod branch
git push origin prod

```
