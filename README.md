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






React Native 
* How to build apk
Ans: 
1. first create expo account on expo website
2. npm install -g eas-cli
3. eas login
4. eas build:configure
5. eas build -p android --profile preview [OR] eas build -p android --profile production 

----------------------
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

java -jar bundletool-all-1.17.1.jar build-apks --bundle=application-07993c7b-460d-464f-932a-6c943c2faa60.aab --output=rentalx.apks --mode=universal --ks=my-release-key.keystore --ks-key-alias=my-key-alias --ks-pass=pass:sanjay@123 --key-pass=pass:sanjay@123












Things need to build app

npx expo prebuild --skip-dependency-update react-native,react

npm install -g eas-cli

eas login

eas build:configure

eas build --platform android

eas build --platform android --profile production

expo apk covert using jar =========== java -jar bundletool.jar build-apks --bundle=filename.aab --output=newfilename.apks --mode=universal

real command ============= java -jar bundletool-all-1.17.1.jar build-apks --bundle=application-87e11464-b949-40a3-86ad-e7658361cee3.aab --output=rentalx.apks --mode=universal

--------------

first create expo account on expo website
npm install -g eas-cli
eas login
eas build:configure
eas build -p android --profile preview [OR] eas build -p android --profile production

----------------------
keytool -genkey -v -keystore my-release-key.keystore -alias my-key-alias -keyalg RSA -keysize 2048 -validity 10000

Enter Valid Information
Provide valid inputs for the distinguished name (DN). If you want to skip a field, type a dot (.) and press ENTER. Here is an example sequence:

First and Last Name: e.g., Sanjay Kumar
Organizational Unit: e.g., IT Department
Organization Name: e.g., Bytegrow Technologies
City or Locality: e.g., Jaipur
State or Province: e.g., Rajasthan
Country Code: e.g., IN (use a valid two-letter country code)

java -jar bundletool-all-1.17.1.jar build-apks --bundle=application-b1a2c2f0-1752-4b4f-ae67-88626aed2231.aab --output=rentalx.apks --mode=universal --ks=my-release-key.keystore --ks-key-alias=my-key-alias --ks-pass=pass:sanjay@123 --key-pass=pass:sanjay@123


