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

## Areas

The file can live in three diferents places in git

- working directory
- staging area(index)
- git repository


notes:

- **hash is generated based on the contents of the file**
- **hash function are one way functions, is not possible to generate the input from the hash**
- **hash, same input always produces the same result**
- **git generates SHA1 hash based on: [content of the file] + [object type] + [object size]**
- **git store file in compressed binary format**
- **filenames for the blobs are stored in tree**
- **checkout means taking file from git repository and putting them on working directory(commit pov)**