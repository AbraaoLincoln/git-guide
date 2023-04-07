# Notes:

- **hash is generated based on the contents of the file**
- **hash function are one way functions, is not possible to generate the input from the hash**
- **hash, same input always produces the same result**
- **git generates SHA1 hash based on: [content of the file] + [object type] + [object size]**
- **git store file in compressed binary format**
- **filenames for the blobs are stored in tree**
- **checkout means taking file from git repository and putting them on working directory(commit pov)**
- **when checkout git updates the working directory and stage area**
- **when commit git writes the files to git repository**
- **when creating a new branch is the same as creating a new reference to a commit**
- **when use checkout git only move the HEAD to the specific commit, it change the contents on HEAD file** 
- **on a clone repo the objects a pack in a package inside .git/objects/pack**