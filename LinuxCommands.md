### TAR
Reference: https://www.marksanborn.net/linux/extract-without-first-directory/
extract tar to a destination folder and extract w/o first directory
`tar xvf foo.tar.gz -C /path/to/dest --strip 1`
unzip to directory
`unzip -d <directory>`

### FIND
find and replace all occuring strings in current folder
`find . -type f -exec sed -i 's#orig_string#replace_string#g' {} +`
get all folders last modified 14 or more days and delete them
```
find /path -maxdepth 1 -mindepth 1 -mtime +14 -type d \
           -exec rsync -a --stats --delete empty/ {} \; -exec rm -r {} \+
```

### GREP
get files where string matches in current folder
`grep -rnw . -e 'text'`

### SCP
`scp user@host1:file user@host2:file2`

### follow tail of growing text file
`tail -f file.txt`
`less +F file.txt`

### RSYNC
faster way of deleting large folder
`rsync -av --delete empty/ foldertodelete/ && rm -rf foldertodelete/`
copy only selected contents of one folder to another
```
rsync -av --include="folder1" \
	 --include="folder1/folderA/***" \
	 --include="folder1/fodlerB/***" \
	 --exclude="*" "$src_dir"/* $dest_dir
```
copy only selected contents of one folder to another with rsync
```
rsync -a --include=/{,'folder1/'{,'folderA/***','folderB/***'}} \
         --exclude="*" "$src_dir"/* $dest_dir
```

### BASH
# Simple array echo
```
array=( 1 2 3 4)
for i in "${array[@]}"
do
  echo $i
done
```

### SED / CUT / AWK / TR
use cut to get only a portion of path. ex. /1/2/3/4 --> /1/2
`echo /1/2/3/4 | cut -d'/' -f1-3`

### GIT
delete remote branch
`git push --delete git@github.com:vinchua/bookish-guide branch`
# revert local commits and return to origin
`git reset --hard origin/branch`
# add subdir of remote repo 
`git remote add -f -t develop --no-tags subdir repo`
# update subdir with changes the repo
`git read-tree --prefix=subdir -u repo/branch:subdir`
# subtree
`git subtree add --prefix subtree-name repo branch`
`git subtree pull --prefix subtree-name repo branch`



