# git-repo

This is just an information repository that contains commands and steps to configure git and push files from local device to remote Repository. Built it for my own reference, but happy if it helped someone!

## Terminal commands

- Use `git config --list` to check the default settings of git for a device.

- Use `git status` to check the current status of the local repository with respect to the remote repository. Shows the changes that still have to be reflected in the remote repository and also guides us through the next steps.

- Use `git add` to add files to the staging area.

- Use `git commit` to commit files to the local repository.

- Use `git push` to publish changes to remote repository.
  
- Use `git init` to initialize an empty local repository.

- Use `git remote add origin <repo_link>` to connect an empty remote repository to the local repository.

- If there is nothing/no branch in an empty repository, you need to use `git push --set-upstream origin main` to create a new branch and push the local repo for the first time.

- Use `new-item -name '<name-of-file>.md'` to create a new-file in the local repo from the terminal.

- Use `git diff` to show changes in file that has not been reflected anywhere.

- Use `git log` to check commit history.

- Use `git restore --staged <file_name>` to restore the state before staging content.

- Use `git revert <commit-id>` to revert back to a previous state of the repo. You can get commit-ids using `git log --oneline`.

## Pushing local files to a remote repository on GitHub.

Follow these steps in the same order to push any file or project to a remote repository from terminal : 

1. [Cloning a Remote repository](#cloning-a-remote-repository)
2. [Pushing files to staging area](#pushing-files-to-staging-area)
3. [Commit locally](#commit-locally)
4. [Push to remote repo](#push-to-remote-repo)
5. [Publish React App to gh-pages](#publish-react-app-to-gh-pages)

## Cloning a Remote repository

To clone/download a git repo to a local device, use
```
git clone <repository_link>
```
    
> will ask for username and password. 

If password doesn't work generate a temporary token from github profile and copy paste that as the password.
  
  - Goto `Developer settings` in Github `account settings` > `Personal access tokens` > `Tokens classic` > `Generate new token` > `Classic Token`
  - Copy paste this token as the password in the terminal.

> After cloning a remote repository, its better to open that folder in VScode and use the Terminal from inside.

## Pushing files to Staging area
Use `git add` to add a file to the staging area so that github knows that you want to save and consider these files in the next commit.
```
git add <filename>
```

You can also use `.` to add all files at the local folder to the staging area.
```
git add .
```

> [!TIP]
> We can always use `git status` to check which files are currently in the staging area or those that have been modified, i.e., it shows the changes that still need to be committed.

## Commit locally

Use `git commit` to commit files to the local repository.
```
git commit -m <message>
```
Changes/files in the staging area are then committed to the local repository using `git commit`.

This means that locally a snapshot has been created of the state of this file.
Using `git status` after this point will tell us that all files have been committed to the local repo but still this is ahead of the branch on the remote repo.

> So we need to push these changes to the remote repository to maintain everything on the same page.

## Push to remote repo

Use `git push` to publish the local repository to the remote repo. 
After that, all changes made locally will be reflected in the remote repository on GitHub.

## Publish React App to gh-pages

Follow these steps to deploy a react application on GitHub Pages:

  - Install the gh-pages package by running the following command:

        npm install gh-pages --save-dev

  - Configure `package.json` file by adding these following lines:

        "homepage": "https://your-username.github.io/your-repo-name",
        "scripts": {
        "predeploy": "npm run build",
        "deploy": "gh-pages -d build"
        }

    > Replace your-username with your GitHub username and your-repo-name with the name of your repository.

  - (Optional) If using Vite build, then add the base path to the `vite.config.js` such as:

      ```
      export default defineConfig({
        plugins: [react()],
        base: '/your-repo-name/'
      })
      ```

  - Deploy your app by running:

      ```
      npm run deploy
      ```

    > This will create a new branch called gh-pages in your repository and push the built files from the build directory to that branch.

  - Enable GitHub Pages: Go to your repository on GitHub and navigate to the `Settings` tab. Scroll down to the `GitHub Pages` section 
    and select the `gh-pages` branch as the source for your GitHub Pages site.

  - Access your deployed app: After a few moments, your React app should be deployed and accessible at the URL mentioned 
    in the `GitHub Pages` section of your repository settings.
