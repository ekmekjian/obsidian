# Git

## History:

- Linus Trovald had been developing the Linux kernel through a [DVCS(Distributed Version Control)](Version%20Control%20Systems.md)  called Bitkeeper. When relations broke between the Linux developers and Bitkeeper they decided to build their own DVCS
- When developing their own DVCS they looked at BitKeeper when deciding on the goals of speed, simple design, Strong support for non-linear development (thousands of parallel branches), fully distributed, and able to handle large projects like the Linux kernel efficiently (speed and data size)
- From these goals came Git

## How does git work?

- Git take all changes made in a commit and creates a snapshot of the entire project and it’s changes
    - When you change a file and commit that change, git will take a snapshot of the project while updating the file that changed and linking all the unchanged files to the snapshot created by the commit.
- Because it works mostly on a local level Git excels in speed. It’s able to recall the history of a project without making a call to the server because the cloning of the project gave the client all it’s versions and history.
- Also makes working offline efficient because commits can be done locally and pushed to the remote branch when connection is established while still maintaining version control.
- Everything in Git is checksummed meaning any changes made within a Git project will be known by Git.
    - SHA-1 is used for checksumming and is calculated based on the contents of a file or directory structure in Git
- Git typically only adds data. Because each commit creates a snapshot, even deletions can be recovered.
- The .git directory of a project is the most important because there is where all the cloned versions of the project are kept

### Three States of Git:

[https://lh4.googleusercontent.com/ZxQ6r7ykwLZ4SuRvNuf2ITZDwwD9s4gPNzinX5HuSzzmcK33zeCmyxh6_ibeL-QIYu44iOc0e0o5JoV2DOYd9fjblsnMcLvpjzpQ-YSSaAFjCQFNlyXvl_j4iDCiT3MPQtJAFhCg](https://lh4.googleusercontent.com/ZxQ6r7ykwLZ4SuRvNuf2ITZDwwD9s4gPNzinX5HuSzzmcK33zeCmyxh6_ibeL-QIYu44iOc0e0o5JoV2DOYd9fjblsnMcLvpjzpQ-YSSaAFjCQFNlyXvl_j4iDCiT3MPQtJAFhCg)

- The three states are modified, staged, and committed
- Modified means that the file has been change and is not committed yet
- Staged means that a file is marked for commit snapshot
- Committed means that the data is store in your local VCS database