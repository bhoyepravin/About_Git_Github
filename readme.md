## In your situation

## Since your push was rejected and you don't want to lose your changes, do not use --hard.
## If your goal is to remove the commit and then pull the latest changes, use:

git reset --soft HEAD~1
git stash
git pull origin main
git stash pop
git add .
git commit -m "Your latest changes"
git push -u origin main
