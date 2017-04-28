# notes

Command line instructions

Git global setup
```
git config --global user.name "Bernard"
git config --global user.email "xiao.bona@qq.com"
```
Create a new repository
```
git clone git@gitlab.dev.com:dev/app-oa.git
cd app-oa
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master
```
Existing folder or Git repository
```
cd existing_folder
git init
git remote add origin git@gitlab.dev.com:dev/app-oa.git
git push -u origin master
```
