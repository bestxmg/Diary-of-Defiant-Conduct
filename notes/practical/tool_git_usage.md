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



To remove a folder from being tracked by Git (i.e., to stop Git from controlling it), you can use the following steps:

### 1. Add the folder to `.gitignore`
First, you should tell Git to ignore the folder by adding it to the `.gitignore` file. This prevents Git from tracking the folder in the future.

- Open or create a `.gitignore` file in the root of your repository.
- Add the folder path to the `.gitignore` file. For example, if the folder is named `myfolder`, add the following line:
  ```
  myfolder/
  ```

### 2. Remove the folder from Git’s index (staging area)
Even after adding the folder to `.gitignore`, Git will still track the folder if it was previously committed. To stop tracking the folder, you need to remove it from Git's index:

- Run the following command:
  ```bash
  git rm -r --cached myfolder
  ```

  This command removes the folder from the staging area but **does not delete the folder from your local file system**.

### 3. Commit the changes
Now, commit the changes to reflect that the folder is no longer tracked by Git:

```bash
git commit -m "Stop tracking folder 'myfolder'"
```

### 4. Push the changes (optional)
If you're working with a remote repository, push the changes to update the remote:

```bash
git push
```

### Summary:
- Add the folder to `.gitignore`.
- Run `git rm -r --cached <folder>` to stop tracking it.
- Commit and push the changes.

This ensures that the folder is no longer tracked by Git and will not be included in future commits, while still remaining on your local machine.

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