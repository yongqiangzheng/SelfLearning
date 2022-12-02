[all-about-git](https://gitee.com/all-about-git)

```
# init 
git init

# add-commit-push
git add .
git commit -m "update"
git push

# create and change branch
git branch -b dev
git checkout dev

# merge other brance
git checkout master
git merge dev
git push

# preserve history branch information
git merge --no-ff dev
git log --graph --pretty=oneline --abbrev-commit
```
