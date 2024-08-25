# basicgitsnippets
<br>
Author sanjayexplorer

<-----------git notes--------------->

git init globaly =>
git config --global user.name "Your New Name"
git config --global user.email "your.new.email@example.com"

how to check git init in system and git details =>
git config --global user.name
git config --global user.email

git add remote to access project from github profile =>
git remote add origin <repository_url>
example : git remote add origin https://github.com/sanjayexplorer/basicgitsnippets

clone a copy of project from github profile =>
git clone <repository_url>
example : git clone https://github.com/sanjayexplorer/basicgitsnippets

check hidden folder in project =>
git ls -a

how to check modified files in project =>
git status


how many status in git =>

untracked(new files that git does not yet track)

modified(changed files)

staged(files that ready to commit)

unmodified(unchanged)

-----map------

untracked(untracked files that new created )
                |
                |
                v
modified(changed files)
                |
                |
                v
staged(files that ready to commit)
                |
                |
                v
unmodified(unchanged)

create file
write in file
check how many files are changed (git status)
then add files to push in repo(git add .)
then commit(git commit -m 'comment')
git push
then check in repo
