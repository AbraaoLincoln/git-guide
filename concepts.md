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

# Merge

From dictionary

- combine or cause to combine to form a single entity

- to combine or join together

Merge is the feature of combine two branches into one. This is needed in the case where we need to incorporate the changes made in one branch into an other branch.

There two ways to merge branch.

- fast forward merge

- 3 way merge

## Receiving branch

branch that receive change made in other branch

## Feature brach

this name is used in this file to name the branch that is being merge with the receiving branch

## Fast forward merge

```
Main branch
------------------------------- >
first_commit <--- second_commit
                        |
                        |   feature branch
                        |   ----------------------------- >
                        | - feature_commit_1 <--- feature_commit_2
```

Fast forward merge is possible when there are no further commits in the receiving branch after the commit where feature branch was created

If possible to do the fast forward merge git will move the pointer of master branch to last commit in the feature branch.

## 3-way Merge

```
Main branch
------------------------------- >
first_commit <--- second_commit <--- third_commit
                        |
                        |   feature branch
                        |   ----------------------------- >
                        | - feature_commit_1 <--- feature_commit_2
```

3-way merge is apply by git when the receiving branch has commits after the base commit of feature branch

git will create a new commit that have two parents commits, one parent is the last commit in the receiving branch e the another is the last commit in the feature branch.

```
Main branch                                                          commit created in the 3-way merge
------------------------------- >                                    ---------------------------------
first_commit <--- second_commit <--- third_commit <----------------- merge_commit
                        |                                                  |
                        |      feature branch                              |
                        |      ----------------------------- >             |
                        | <--- feature_commit_1 <--- feature_commit_2 <----|
```
### Nearest Common Commit Ancestor

the second_commit is the nearest common commit ancestor

### Merge commit

git tries to make a commit with all the change of the feature branch, this commit is the merge commit.

- 3-way merge

if in the process of doing the 3-way merge, the same file was change in the receiving branch and feature branch, then git will ask to resolve the merge conflic

### Recursive startegy

git look for comun ancetor commit and create the merge commit

### The Process to merge two branch

```
git checkout <receiving_branch>

git merge <feature_branch>
```

## Merge Conflict

Merge conflict can happen when change the same file in differents branches.

- merge conflict only happens when there is new commits in the base branch(branch witch the current is based of)

- merge conflict doesn't happen in fast forward merge.

- merge conflict can appear in the 3-way merge

## Staging area

```
git ls-files -s
                                                v
100644 83db48f84ec878fbfb30b46d16630e944e34f205 1	file1.txt
100644 49a657e0b894f67e271e9a65768c189e64626202 2	file1.txt
100644 b4681d1f56157994ebb8eb6308d3f73eda58d580 3	file1.txt
```

| version | description |
|---------|-------------|
| 1 | version of the file in the nearest common ancestor commit, the initial version of both branches |
| 2 | version of the file in the receiving branch |
| 3 | version of the file in the feature branch |

## .git/MERGE_HEAD

pointer to the last commit in the feature branch