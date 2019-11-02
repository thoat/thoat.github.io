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

* **Git config**:
   1. `--system`: values from file `/etc/gitconfig`. Applied to every user on the system & all their repo's.
   2. `--global`: values from file `~/.gitconfig` or `~/.config/git/config`. Applied specifically to me & all my repo's on my system.
   3. `--local`: values from file `.git/config` of the current repo. Applied to that single repo.

   (3) trumps (2). (2) trumps (1).
   
   * My system-level config:
      * Windows: at `C:/Program Files/Git/mingw64/etc/gitconfig`.
      * (Git for Windows 2.x) another file at `"C:\\ProgramData/Git/config`. This config file can only be changed by `git config -f <file>` as an admin.
      * WSL: no file yet.
   
   * My global-level config:
      * Windows: at `C:\Users\$USER\.gitconfig`.
      * WSL: at `~/.gitconfig`.
   
(credit: https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)

----------

To set up a Git account for work (separate from this personal Git account):

* If push/pull via HTTPS: 

   1. Commits correctly authored: set local git user.email: 
   
   ```
   # inside the work repo
   $ git config --local user.email "work.email@company.com"
   $ git config --local user.name "work.name" # optional
   ```
   
   2. Push/pull as the correct user: enter the work username and password when prompted
      
* If push/pull via SSH:
  
  1. Commits correctly authored (see above)
  
  2. Push/pull as the correct user:
  
     1. Generate a new pair of SSH key-value: `~/.ssh/id_rsa_companyA`
     
     2. Set host in `~/.ssh/config`, or else I'll need to use this lengthy command: `GIT_SSH_COMMAND="ssh -i ~/.ssh/id_rsa_companyA" git push`. This helps SSH locate the correct key-value pair.
     
     ```
     # Default GitHub
     Host github.com
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa

     # Professional github alias
     Host newsubdomain
        HostName github.com
        User git
        IdentityFile ~/.ssh/id_rsa_companyA
     ```
     
     3. Configure my remote URL using the host set in the previous step: 
     
     ```
     # from git@github.com:name/repo.git
     $ git remote set-url origin git@newsubdomain:name/repo.git
     ```

(credit: https://stackoverflow.com/a/33079036)

----------

* To update Git on Ubuntu WSL 16.04 (because it came packaged with Git 2.7.4): 

```
$ sudo apt update
$ sudo apt -y install make libssl-dev libghc-zlib-dev libcurl4-gnutls-dev libexpat1-dev gettext unzip
$ git clone https://github.com/git/git.git git-source
$ cd git-source
$ make prefix=/usr/local all # seems to make files only
$ sudo make prefix=/usr/local install # actually installs stuff?

# restart the terminal to check the new git version: git --version
```

(credit: https://jimfrenette.com/2018/07/git-updates-for-windows-powershell-and-wsl-ubuntu/)

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

---

* To sort contents of the file `greatest.txt` and print them:

```
cat greatest.txt | sort
```
   
