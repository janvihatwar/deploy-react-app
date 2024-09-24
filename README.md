# Deploying Your React App to GitHub Pages with react-gh-pages

## Introduction
In today’s world, getting your web applications online is important. If you’ve created a cool React app and want to share it, deploying it on GitHub Pages is a great choice. This guide will show you how to easily deploy your React app using the react-gh-pages package, making it simple to share your work.

## What is GitHub Pages?
GitHub Pages is a free service from GitHub that lets you host simple websites directly from your repositories. It’s great for showcasing personal projects, portfolios, and documentation.

## Why Use react-gh-pages?
The react-gh-pages package makes deploying React apps quick and easy. With just a few commands, you can move your app from development to a live website, making it accessible to anyone.

## Prerequisites

**Node.js and npm [Node and npm](https://nodejs.org/en/download/):** Download and install from nodejs.org. These are essential for creating and building your React app.

**[Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git):** Make sure you have Git installed to manage your repositories.

**[GitHub](https://github.com/signup) :** Create one if you haven't already.

**GitHub Repository:** Set up a new repository where your app will be hosted.

## Procedure

### 1. Create an **empty** repository on GitHub

1. Sign into your GitHub account.
2. Visit the [Create a new repository](https://github.com/new) form.
3. Fill in the form as follows:
    - **Repository name:** You can enter any name you want\*.
        
   - **Repository privacy:** Select _Public_ (or _Private_\*).

   - **Initialize repository:** Leave all checkboxes empty.

### 2. Create a React app

1. Create a React app named `my-app`:
    ```shell
    $ npx create-react-app my-app
    ```
    
2. Enter the newly-created folder:
  
    ```shell
    $ cd my-app
    ```
At this point, there is a React app on your computer and you are in the folder that contains its source code. All of the remaining commands shown in this tutorial can be run from that folder.


### 3. Install the `gh-pages` npm package

1. Install the [`gh-pages`](https://github.com/tschaub/gh-pages) npm package and designate it as a [development dependency](https://docs.npmjs.com/specifying-dependencies-and-devdependencies-in-a-package-json-file):
 
    ```shell
    $ npm install gh-pages --save-dev
    ```

At this point, the `gh-pages` npm package is installed on your computer and the React app's dependence upon it is documented in the React app's `package.json` file.

### 4. Add a `homepage` property to the `package.json` file

1. Open the `package.json` file in a text editor.
   
    ```shell
    $ vi package.json
    ```

    > In this tutorial, the text editor I'll be using is [vi](https://www.vim.org/). You can use any text editor you want; for example, [Visual Studio Code](https://code.visualstudio.com/).


2. Add a `predeploy` property and a `deploy` property to the `scripts` object:

    ```diff
    "scripts": {
    +   "predeploy": "npm run build",
    +   "deploy": "gh-pages -d build",
        "start": "react-scripts start",
        "build": "react-scripts build",
    ```

At this point, the  React app's `package.json` file includes deployment scripts.

### 6. Add a "remote" that points to the GitHub repository

1. Add a "[remote](https://git-scm.com/docs/git-remote)" to the local Git repository.

    You can do that by issuing a command in this format: 
    
    ```shell
    $ git remote add origin https://github.com/{username}/{repo-name}.git
    ```
At this point, the local repository has a "remote" whose URL points to the GitHub repository you created in Step 1.


### 7. Push the React app to the GitHub repository

1. Push the React app to the GitHub repository

    ```shell
    $ npm run deploy
    ```
At this point, the GitHub repository contains a branch named `gh-pages`, which contains the files that make up the distributable version of the React app. However, we haven't configured GitHub Pages to _serve_ those files yet.


### 8. Configure GitHub Pages
After deploying your app, you need to configure GitHub Pages to serve the files from the gh-pages branch. Follow these steps:

- #### Navigate to Your GitHub Repository:

Open your web browser and go to your GitHub repository.

- #### Access the Settings:
Click on the "Settings" tab located at the top of the repository page.

- #### Locate the Pages Settings:
In the left sidebar, scroll down to the "Code and automation" section.

- #### Click on "Pages".
Configure the Build and Deployment Settings:

   1. **Source**: Deploy from a branch
   2. **Branch**: 
      - Branch: `gh-pages`
      - Folder: `/ (root)`

After selecting the options, click the "Save" button at the bottom of the page.
#### Verify Your Deployment:

After saving, GitHub will start deploying your app.

## It may take a few minutes(approx 1).

***Once complete, GitHub will provide a URL to access your deployed app.***

**Note:*** You can also check the status of your deployment on the same GitHub Pages settings page.

### 9. (Optional) Store the React app's _source code_ on GitHub

In this step, I'll show you how you can store the source code of the React app on GitHub.

 Commit the changes you made while you were following this tutorial, to the `master` branch of the local Git repository; then, push that branch up to the `master` branch of the GitHub repository.

```shell
 $ git init
 $ git status 
 $ git add .
 $ git commit -m "Configure React app for deployment to GitHub Pages"
 $ git push origin master

```

 I recommend exploring the GitHub repository at this point. It will have two branches: `master` and `gh-pages`. The `master` branch will contain the React app's source code, while the `gh-pages` branch will contain the distributable version of the React app.


### Tips for Managing Files on GitHub
- ***Organize with Folders:*** You can create folders within your repository to keep things organized. Use the "Create new file" option and specify a folder name in the file path (e.g., folder-name/file-name).

- ***Edit Files:*** To edit any file directly on GitHub, navigate to the file and click the pencil icon to enter edit mode.

- ***Delete Files:*** To delete a file, navigate to it and click the trash can icon. You will need to commit this change as well.


**Great job!** You’ve successfully deployed your React app to GitHub Pages using the react-gh-pages package. 
In this guide, you learned how to:
- Create a React app and get it ready for deployment.
- Install the necessary packages and set up your project.
- Upload files to your GitHub repository.
- Configure GitHub Pages to host your app.
- Now your app is live and can be accessed by anyone! Feel free to share your work and keep exploring new features for your app.

If you run into any issues, you can always come back to this guide or check out the [GitHub Pages documentation](https://docs.github.com/en/pages) and the [Create React App documentation](https://create-react-app.dev/docs/getting-started/).
