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
git config --global user.name name

git config --global user.email email
```

💻 To see configs

```
git config --list
```

## Daily commands

💻 Show the current status of git repository

```
git status
```

💻 Add files to staging area

```
git add
```

💻 Write changes to git repository

```
git commit
```

💻 Show history of commits

```
git log
```

💻 Checkout commit or branch

```
git checkout 
```
