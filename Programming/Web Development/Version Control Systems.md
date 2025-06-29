# Version Control Systems

## What is version control?

- A system that records changes to a file or set of files over time so that you can recall specific version later

### Benefits

- Allows for file/project to revert to a previous state
    - A crash that causes the program to not work when it did can be reverted to a state when it did work
    - A missing file can be restored
- Can be used to keep track of changes and by who

## Version Control Types:

### Local Version Control Systems

- Simple method of copying files and copying into another folder locally
    - Backs-ups like this would name the folders with time stamps and probably notes (If done correctly)
- Flaws:
    - It is easy to forget which folder you were in when making copies as well as moving/writing the incorrect file
- Solution:
    - Created a simple database that kept all changes to files under revision control


![[Pasted image 20220317114207.png]]

### Centralized Version Control Systems:

- A solution for collaborating on projects
- A single server that contained all the versions for a project was used for clients to checkout files
- 
- Benefits:
    - Versions on a server can show what each version is trying to accomplish
    - Admins have an easier time working with the version being in one location as opposed to copies on every local machine
- Flaws:
    - If anything were to happen to the server or it’s hard drive all work would be lost

### Distributed Version Control Systems:

- Do more than just offer a way to back and pull changes. You got the FULL project and it’s versions when cloned.
- Clones are full back-ups
- Allows for more complex collaborations with not just different projects but their versions
- Benefits:
    - If a server were to die anyone with a clone of the project could restore the repo to the new server with all version originally made.

![[Pasted image 20220317114226.png]]