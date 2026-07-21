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
