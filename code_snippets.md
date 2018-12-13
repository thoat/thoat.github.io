# Convenient code snippets

* To remove git tracking in a local folder: go inside that folder and type
```
$ rm -rf .git
```
(credit: Stack Over Flow)

----------

* To clone a fresh version from GitHub and replace your current git repo:
```
$ cd ..
$ rm -rf <repo-name>
$ git clone <URL> <repo-name>
```

----------

* To unstage a file and keep it (aka when trying to pull and getting warned that some untracked files will be overwritten):
```
$ git reset name_of_file
```
(credit: https://stackoverflow.com/a/4308645) -- see there for more details cleaning up afterwards

----------

* To revert a pushed commit:
```
$ git clone <url> my-clone
$ cd my-clone
$ git log  //to find the commit id
$ git revert <commit-id>
$ git push
```
(credit: https://www.quora.com/How-do-I-revert-a-GitHub-commit-on-the-website-Is-there-a-link-somewhere-to-revert-a-commit-Or-do-I-need-to-do-this-somehow-from-the-command-line-I-never-downloaded-the-fork-to-my-local-machine-though)

----------

* To create AND switch to a different remote branch: (ignore -b if your branch already exists)
```
$ git checkout -b iss53
Switched to a new branch "iss53"
```
This is shorthand for:
```
$ git branch iss53
$ git checkout iss53
```
(credit: https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)

----------

* To fetch a branch:
  * Fetch all remote branches: `$ git fetch origin`
  * (optional) Pull changes to your current change: `$ git pull`
  * Check out the branch you are interested in (this will give you a local working copy of that branch):
    `$ git checkout -b thatbranch origin/thatbranch` 
    OR
    `$ git branch thatbranch origin/thatbranch`    
    
    (BUT DOES THIS ASSUME THAT THIS BRANCH HAS NOT EXISTED IN YOUR LOCAL MACHINE?)
    
(credit: https://gist.github.com/markSci5/5916003)

----------

* To manage branches:
  * See the list of my local branches: `$ git branch`
  * See the list of remote branches: `$ git branch -r`
  * To make a remote branch a local branch: `$ git checkout that-new-remote-branch`

(credit: https://gist.github.com/blackfalcon/8428401 KEEP REFERRING BACK TO THIS to review GitHub Worklow practice)

----------

* To install package, check package's version, etc. in Linux Ubuntu:

```
$ sudo apt-get update && apt-get upgrade
$ sudo apt-get install <packagename>
$ <packagename> -v or <packagename> --version
$ apt-cache madison <packagename> or apt-cache policy <packagename>
```

----------

* To completely remove a package on Linux Ubuntu (and bring back the computer's state before its installation):
```
sudo apt-get --purge autoremove <pkgname>
```
  Just the package & its dependencies: 
```
sudo apt-get --purge remove <pkgname>
```
(credit: https://askubuntu.com/a/151943)

----------

* To change colors in the Shell (incomplete solution):
   https://askubuntu.com/a/466203
   
----------
   
* If eslint gives Windows trouble ("Expected LF but found CRLF"): add this line to `eslintrc` under `rules` section: 
```
"linebreak-style": 0,
"global-require": 0,
```
       
----------

* To kill multiple Node processes use this command on windows cmd: 
```
$ taskkill /im node.exe /f
```

----------

* To view version of python packages or modules:
```
$ pip list OR
$ pip show <package-name>
```

----------

* To find out if some package(s) is/are already installed:
```
$ dpkg -l | grep packagename, OR
$ dpkg -l | grep 'packageA\|packageB'  # use backlash to protect the alteration sign
```

----------

* To convert CRLF to LF on all JavaScript files in folders and subfolders, excluding node_modules folder:
```
$ find . -not \( -path ./client/node_modules -prune \) -not \( -path ./server/node_modules-prune \) -name \*.js -print0 | xargs -0 dos2unix
```
(source on chaining files into dos2unix: https://stackoverflow.com/a/11929475; source on excluding files for find: https://stackoverflow.com/a/16595367)

----------

* To _print_ the output of `ls`:

```
$ echo $(ls -l)
total 8 -rw-rw-r-- 1 bo bo 13 Aug 21 12:57 t.sh -rw-rw-r-- 1 bo bo 78 Aug 21 12:57 u.sh

$ echo "$(ls -l)"
total 8
 -rw-rw-r--  1 bo bo  13 Aug 21 12:57 t.sh
 -rw-rw-r--  1 bo bo  78 Aug 21 12:57 u.sh
 ```
 (credit: http://tldp.org/LDP/abs/html/quoting.html#QUOTINGREF)
 
 ---
 
 * To search all files recursively for string "Alexandr" (notice the dot at the end):
 
```
grep -R Alexandr .
```
   