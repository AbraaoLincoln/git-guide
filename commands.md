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

