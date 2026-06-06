# Learn Git and Github with me!  
this is all my notes from where I try to learn what is git from watching or reading a bucnh of stuffs. I will link everything I read or watch below.

Why use github or any other remote repositories, think of it like using google drive instead of your gallery.
If you are only saving all your files locally it will be gone forever if the device broke but if you use github or something like it, you are sure it will not be gone even if you change your device.
You can also use github to instead of sending your file everytime to your workmates, you can just instead upload it and show it to them and they can even edit it or something.

This has 2 main idea, the push and pull
- **Push**, this means you upload what is in your local computer into github which updates your work already in there
- **Pull**, this means you now download what is in your github into your local computer which now updates what you currently have

## Git Core Structure
Git has 2 main parts:

- **Local** refers to my computer where I do all my codes which in this case my linux laptop
- **Remote** refers to the cloud where I will upload my work, this usually means github where I will be posting this publicly

### Local Git
- **Working directory**, this is the folder where I do all my work
- **Local Repository**, this is where my files go whenever I save a file but it doesn't save things permanently right away
- **Stage**, this is like the middle ground between save repository and working directory
- **Commit**, this means you want to permanently save your works after checking everything
- **Repository**, this is where all the version of files are and all other details like when it was change and who made it

### Local Git's Workflow
1. **Working Directory** → The folder where you are making your project
2. **Stage** → My changes are ready they can go to the next step
3. **Local Repository** → Temporary area where files sit between **Working Directory** and **Repository Save**

## How to make a Git Repository
### Local Machine Repository 
1. Make a folder in your local machine
2. If you are using the **terminal**, use cd command to go to your folder then type git init. But if you are using **VS Code** you can open your folder directly then press ``Ctrl + ` `` to open up a terminal inside then type git init or you can just go to source control to initialize it
### Remote Repository
1. Make a repository on Github
2. Then click the green button with text "<> Code" on it
3. You will see a bunch of option but select the HTTPS then copy the link below it
4. Then in **terminal** or **VS Code** you select your folder then type in `git clone <github url>` to then clone the specified repository into your own local machine

## Commands:
`git clone <github url>` - this clone the whole specified github repo into your selected folder
`git status` - shows summary of everything. What has changed, which files are new, and which files are modified.  
`git add <file name>` - adds a specific file to the **Stage** part of git and prepares it for the next commit. This is called Stages or Staged  
`git add -A` or `git add --all` - also stages the file but instead of only one it stages all at the same time  
`git add .` - this also stages files but only everything inside my current directory instead of the whole project  
`git add *` - stages only all new or modified files and not including the deleted ones  
`git add *.txt` - this stages every .txt file, but still excluding the delete ones. You can use any file extension here.  
`git reset` - this resets all you did even if they are staged  
`git reset HEAD~` - this will undo the last commit and bring everything in working directory


---
Source: https://youtu.be/mAFoROnOfHs