```
   _____                                          _     
  / ____|                                        | |    
 | |     ___  _ __ ___  _ __ ___   __ _ _ __   __| |___ 
 | |    / _ \| '_ ` _ \| '_ ` _ \ / _` | '_ \ / _` / __|
 | |___| (_) | | | | | | | | | | | (_| | | | | (_| \__ \
  \_____\___/|_| |_| |_|_| |_| |_|\__,_|_| |_|\__,_|___/
   
```

:computer: Initialize a ampty git repository

```
git init
```

## Low level commands

:computer: Create a new Blod object in git structure

```
git hash-object
```

:computer: Create a git Tree object

```
git maketree
```

:computer: Read git objects

```
# Get the content of object
git cat-file -p hash 

# Get the size of the object
git cat-file -s hash 

# Get the type of object
git cat-file -t hash 
```

:computer: List the files in the staging area

```
git ls-files -s
```

:computer: Put files from git repository on staging area

```
git read-tree [hash of tree object]
```

:computer: Put files from staging area on working directory

```
git checkout-index -a
```

## Config commands

:computer: To set name and email globally

```
git config --global user.name name

git config --global user.email email
```

:computer: To see configs

```
git config --list
```

## Daily commands

:computer: Show the status of git repository

```
git status
```