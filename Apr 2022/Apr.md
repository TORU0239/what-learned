# Apr 2022
### 13 Apr
About Firebase App Distribution
1. The app should be reviewed
2. Developers account should be same as Firebase console owner
3. The app has to be linked with Google Play and Firebase
4. After that, Firebase can distribute the app on the track of release.


### 18 Apr
Simple but forgetful things to myself, about forceful update.

**git reset**
This reset has 3 types, normal reset, soft reset, hard reset

`git reset <commit hashtag>`
* changes will be added in unstaged area

`git reset --soft <commit hashtag>`
* changes will be added in staged area, so it will be reverted when running `git commit`.

`git reset --hard <commit hashtag>`
* Changes will be added in neither unstaged nor staged. Hasta La Vista! 
* Hence it's not recommended though, but sometimes we may encounter that we need to discard changes by someone's mistake. be careful.
