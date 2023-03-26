```
   _____                                          _     
  / ____|                                        | |    
 | |     ___  _ __ ___  _ __ ___   __ _ _ __   __| |___ 
 | |    / _ \| '_ ` _ \| '_ ` _ \ / _` | '_ \ / _` / __|
 | |___| (_) | | | | | | | | | | | (_| | | | | (_| \__ \
  \_____\___/|_| |_| |_|_| |_| |_|\__,_|_| |_|\__,_|___/
   
```

💻 Initialize a ampty git repository

```
git init
```

## Low level commands

💻 Create a new Blod object in git structure

```
git hash-object
```

💻 Create a git Tree object

```
git maketree
```

💻 Read git objects

```
# Get the content of object
git cat-file -p hash 

# Get the size of the object
git cat-file -s hash 

# Get the type of object
git cat-file -t hash 
```

💻 List the files in the staging area

```
git ls-files -s
```

💻 Put files from git repository on staging area

```
git read-tree [hash of tree object]
```

💻 Put files from staging area on working directory

```
git checkout-index -a
```

💻 Remove file from staging area

```
git rm --cached filename
```

## Config commands

💻 To set name and email globally

```
git config --global user.name "name"

git config --global user.email "email"
```

💻 To set name and email only to git repository which are being used

```
git config user.name "name"

git config user.email "email"
```

💻 To see configs

```
git config --list
```

💻 To unpack objects

```
git unpack-objects

cat pack-123 | git unpack-objects
```

## Daily commands

💻 Show the current status of git repository

```
git status
```

💻 Add files to staging area

```
git add file1 file2

git add .
```

💻 Write changes to git repository

```
git commit -m "commit message"

# -a add files to stage area
git commit -m "commit message" -a
```

💻 Show history of commits

```
git log
```

💻 Checkout commit or branch

```
git checkout commit | branch
```

💻 Clone a git repo

```
git clone location
```

💻 Show difference between version

```
# difference between working directtory and git repo
git diff

# difference between branches
git diff branch1 branch2

# difference between specific commits
git diff hash-commit-1 hash-commit-2
```

### Branch Managemnt

💻 List all local branches

```
git branch
```

💻 Create a new Branch

```
git branch name
```

💻 Checkout to specific Branch

```
git checkout name
```

💻 Delete a specific Branch

```
git branch -d name
```

💻 Rename specific Branch

```
git branch -m old-name new-name
```

💻 Rename the current Branch

```
git branch -m new-name
```

💻 Create and checkout to the specific Branch

```
git checkout -b name
```