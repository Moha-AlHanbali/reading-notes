[Home](README.md)

<br>

# Introduction to  Git

<br>

- ## The Concept of Git
The simplest way to put Git in, is to think of it as an Active Archiving System, it keeps every single record of every single process performed on all data within it.
You can check original data form, edits applied onto it, others' contributionsm, and have a place to store all of this.

<br>


- ## The Purpose of Git
The main reason to use Git is to keep and work with all versions of your work, aka Version Control System `VCS`. Whether it be for documenation purposes, re-visitng and editing past works, keeping back-ups or branching your work into different paths, you need a system to keep everything recoded, organized and in track.

<br>

- ## Why Should I Use Git?
In addition to having constant back-ups for your work, Git allows you to keep track of your it at all stages, in both solo and team based projects. You can work offline, and publish your work when it's ready to be shared, recieve and share contributions at any stage and time in team projects, and have the ability ro revert changes at any given time.

<br>

- ## Working with Git
Working with Git is absolutely easy, even without using `Git GUI`. You just need to have a Cloud VCS Host Account (GitHub in this case,), and install Git on your local machine. From here, these steps will almost always be the same from here on (using simple analogy):
- Get the link of the Repository you want to work on.
- Use a Command Line Interface `CLI` (Windows Shell, Ubuntu or any terminal of your choice) to enter the following commands (often depicted as `ACP` workflow).
- Get into the directory you'll be using and use `git clone` command to "Sync and Download" Repository's content there.
- Continue your work on your local machine in whatever way you like.
- Once you want to "share" your work on GitHub, use the terminal to "select and copy" the target items using `git add` command followed by `.` for everything or specific file names.
- Now commit a version to identify these changes using `git commit -m "*"` replacing the * with the commit title/comment.
- Finally, use `git push origin main` where origin is GitHub and main stands for the branch you're working in.

<br>

- ## Tips and Troubleshooting
  - Use `git stash` to keep your changes and modifications hidden as a draft, and use `git stash apply` to retrieve them.

  - Use `git pull` to update your `Local Machine` version with any modifications added on GitHub.

  - Use `git status` to check the status of your files.
  
   ```
   [main !] means that some modification was applied but not commited. 
  
   [main *] means that some modification was commited but not yet pushed.

   ```
   - Use `git remote -v` to list the URLs of repositories you're working on in addition to their corresponding *hosts* names.
   - Use `git remote rename` followed by the current shortname and the new name to rename *the host* shortname, in this format:
   > git remote rename **old new**
   - Use `git remote add` and `git remote rm` too add/remove remote names (*hosts*). Use this format:
   > git remote add **newname**
   
   > git remote rm **oldname**
   