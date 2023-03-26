```
   _____                           _       
  / ____|                         | |      
 | |     ___  _ __   ___ ___ _ __ | |_ ___ 
 | |    / _ \| '_ \ / __/ _ \ '_ \| __/ __|
 | |___| (_) | | | | (_|  __/ |_) | |_\__ \
  \_____\___/|_| |_|\___\___| .__/ \__|___/
                            | |            
                            |_|            
```

# Git Objects

## Types

- Blob 

   - git store files with any extension, file a store as Blod so Blod represent a file
   - blod dont store name of the file
   - the size and type are store inside the blod

- Tree 

   Tree in git store information about directories, Tree in git maybe a set of Blob or set of blod and other Tree, Tree is the represatation of directories in git

- Commit

   Commit helps to keep diferent version of the project

- Annotated tag

   Persistent text pointer to a specific commit

## Structure

The structure of a git object cosists of four fields:

- Object type
- Object size
- Delimiter
- Content

The hash is gerenated following
```
#syntax
type sizeDelimiterContent

#example: blob 6\0Hello

echo "Hello" | git hash-object --stdin
e965047ad7c57865823c7d992b1d046ea66edf78

echo "blob 6\0Hello" | shasum
e965047ad7c57865823c7d992b1d046ea66edf78
```
### Tree

Tree contains a set of links to other blobs and Tree, each line of the file is composed of four fields

```
permitions type hash    [name of the file/directory]
```

There are six permitions, git needs to know the permition when gonna create the files

| code | description |
|------|-------------|
|040000|Directory|
|100644|Regular non-executable file|
|100664|Regular non-executable group-writeable file|
|100755|Regular executable file|
|120000|Symbolic link|
|160000|Gitlink|

### Commit

Each commit has its own hash, commit store diferents version(snapshots) of the project. Commit is just "wrapper" for tree objects and contains a pointer to a specific tree

The content are:

- author name and email
- description
- pointer to a tree object
- parent(optional)

# Areas

The file can live in three diferents places in git

- **working directory**
   
   files when in this area can have the following states

   - Untracked
   - Modified
   - Unmodified

- **staging area(index)**

   files when in this area can have the following states

   - Staged
   - Unmodified

- **git repository**

   files when in this area can have the following states

   - Unmodified

## Tracking status

Every file in git may have one of tracking state

- Untracked -> new files that do not exists on git repository
- Unmodified
- Modified
- Staged
- deleted is like modified

if a file has been created its status is untracked, when with state of modified, staged or unmodified is been track by git.

> git add file -> stated

> git commit -> unmodified

> any change in the file -> modified

# Branchs

Branch is a text reference to a specific commit (a pointer to a commit). 

- default branch is master

   the command below can be used to set the name for the default branch

   ```
   git config --global init.defaultBranch name
   ```

- pointers for all branchs are located in .git/refs/heads folder

   - the content of files located in .git/refs/heads are the hash of the commit that the branch pointers to.

   - the hash is from the last commit of branch

- current branch track new commits

- branch pointer move automatically after every new commit

- current branch can be only one

## Head

Head is a pointer to a specific commit, git uses it to know wich branch is the current one.

- can only be one head

- Head is locally significant(only matter on local git repo)

- The pointer is located in the .git/HEAD file

   the content are: ref: refs/heads/branchName

   if in detached mode: hash of commit

- to change reference to a specific branch: git checkout branch-name

- to change reference to a specific commit: git checkout commit-hash

### Detached HEAD

This state means that the HEAD is not point to a branch, but direct to a specific commit