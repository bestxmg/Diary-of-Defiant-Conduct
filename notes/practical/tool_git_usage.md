## Knowledge about Git🐶

### 1. Install and config git

**step 1:** install git
```bash
yum install git
```

**step 2:** config git
```bash
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```
**step 3** connect to GitHub with SSH
```bash
ssh-keygen -t ed25519 -C "your_email@example.com" # if it's your first time generate SSH. You can just type enter until end.
vim ~/.ssh/id_ed25519.pub # copy the text in this file, then open github to add new SSH key, paste the text in the textbox named "key"
```
[Link of adding new SSH key](https://github.com/settings/ssh/new)
### 2.  .gitignore file

The .gitignore file ,created in the git repository, is use to specify those files or folders we don't want it to be managed by git. We can use a .gitignore file in following steps:

step 1: create a .gitignore file
```bash
vim .gitignore # Attention, the dot before gitignore can't be omitted.
```

step 2: edit .gitignore file
```
# the relative path of the file you don't want to be manage by git
notes/practical/temp_md.md
```

After finishing the steps above, the modification of that file will be visible to git management.

---
### 3.
### 4.
### 5.
### 6.
### 7.
### 8.
### 9.
### 10.
### 11.
### 12.
### 13.
### 14.
### 15.
### 16.
### 17.
### 18.
### 19.
### 20.
### 21.
### 22.
### 23.
### 24.
### 25.
### 26.
### 27.
### 28.
### 29.
### 30.
### 31.
### 32.