# Learn Git and Github with me!  
this is all my notes from where I try to learn what is git from watching or reading a bucnh of stuffs. I will link everything I read or watch below.

Why use github or any other remote repositories, think of it like using google drive instead of your gallery.
If you are only saving all your files locally it will be gone forever if the device broke but if you use github or something like it, you are sure it will not be gone even if you change your device.
You can also use github to instead of sending your file everytime to your workmates, you can just instead upload it and show it to them and they can even edit it or something.

## Local and Remote Repository Communication
- **Push**, this means you upload what is in your local computer into github which updates your work already in there
- **Pull**, this means you  download what is in your github into your local computer which now updates what you currently have
- **Fetch**, this mean you download what is in github but instead of it merging, it just sits with your local working directory

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

## Branching
What this basically means is, instead of overwriting your file and losing the ability to go back to it, you instead make another branch which where you can test and experiment if it will work in the main branch.

The **'main' branch** is the original branch. This is where you don't overwrite things or else it might break. Think of it like this, there is a beta and released updates of the game. Developers don't just add things into the game, instead they make a branch or clone of that game then test everything there then whenever you are certain everything is fine then you **merge** the beta game into the actual game. This allows you to have the option to try first then if its not working or you don't like it anymore you can just delete the beta game and use the original game.

**Merge**, this just means combining the branches into one. Git also manages everything seamlessly so you wouldn't see any file you created in one branch into another one unless you merge it.

**Merge Confilict**, this happens if you merge 2 branches but both of them modified a specific file into something different so git doesn't know which to keep. To solve this, you manually edit the file. Git marks the conflicting line so you can see it easily then you decide what to do but don't forget to also remove the markers.

## Revert vs Reset
this 2 things brings you back to the specific commit you want to go but they are quite different.

- **Reset**, this reset your commit and discards everything you did after the specified commit you want to go back to and this doesn't leave any records that you goes back
- **Revert**, this reverts back your commit into the last commit before it or your specified commit. But instead of discarding everything this makes another commit which records what happened and the commits you have after the specified commit will not be deleted

## Commands:
`git clone <github url>` - this clone the whole specified github repo into your selected folder
`git status` - shows summary of everything. What has changed, which files are new, and which files are modified.  
`git add <file name>` - adds a specific file to the **Stage** part of git and prepares it for the next commit. This is called Stages or Staged  
`git add -A` or `git add --all` - also stages the file but instead of only one it stages all at the same time  
`git add .` - this also stages files but only everything inside my current directory instead of the whole project  
`git add *` - stages only all new or modified files and not including the deleted ones  
`git add *.txt` - this stages every .txt file, but still excluding the delete ones. You can use any file extension here.  
`git reset` - this resets all you did even if they are staged  
`git reset --hard` - this resets everything even if a file is deleted it will come back  
`git reset HEAD~` - this will undo the last commit and bring everything in working directory  
`git rm <file name>` - this deletes a file then stages it right away but you can't delete a non commited file  
`git rm -f <file name>` - this deletes a file even if its non commited. Bascially for the system to delete this file  
`git rm --cached <file name>` - this removes the file from the **Stage** but still exists in **Working directory** basically untracking it  
`git rm -r <folder name>` - this now deletes everything in the folder including the files inside it  
`git rm <folder name>` - this deletes the folder but keeps the files inside of it  
`git log` - prints and lets you view all git commits  
`git log --oneline` - this also let you view all commits but this makes everything simpler  
`git branch` - shows all existing branches  
`git branch <branch name>` - this makes a new branch depending on the name you put in it. This is basically a clone of the main branch  
`git checkout <branch name>` - this makes you switch from your current branch to the specified branch  
`git checkout <commit id>` - this switches you to a specific commit base on the id. You can get the branch id by using the "git log" command  
`git merge <branch name> -m "Your Message"` - this merges the specified branch into the branch you are currently in but this doesn't modify the specified branch  
`git diff <commit id 1> <commit id 2>` - this compares 2 commit versions and shows you everything that has changed  
`git push origin <branch name>` - this pushes your local repository into github or any remote repository  
`git fetch` - this fetches your remote repository and adds them to your local repository but you can't see it  
`git merge` - you run this after you fetch so you can see all things you added  
`git pull` - this automatically do both the fetch and merge at the same time  
`git restore <folder or file name>` - this discard everything you did on that folder or file that is still not staged  
`git restore --staged <folder or file name>` - this now removes files from the **Stage** area but don't touch anything it just comes back to the working directory  
`git stash` - this saves your unfinished work without commiting it if you suddenly want to switch branch so you don't lose your work  
`git stash list` - this lists all your current stash  
`git stash pop` - this bring your newest stash into your working directory then also removes itself from the stash list. If you want to pop specific stash add the ID you can see in the "git stash list" next to this command  
`git stash apply` - this is like pop but this doesn't remove itself from the stash so you can always use that specific stash again as long as you don't pop it. If you want to apply specific stash add the ID you can see in the "git stash list" next to this command    
`git stash drop` - this deletes your newest stash.  If you want to drop specific stash add the ID you can see in the "git stash list" next to this command    
`git revert <commit id>` - this revert your commit to the commit before it but it doesn't delete this or the commit before it instead it makes a new commit  
`git rebase <branch name>` - this is like merging a branch to another but instead of it recording it, it just smoothly merges it. But this re writes existing commit history so beware on using it  

---
Source: https://youtu.be/mAFoROnOfHs