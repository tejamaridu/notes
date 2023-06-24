 
# GIT

 ### Getting & Setting up 

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone <git_hub_url>` | Create a local copy of a remote repository |
| `git config -- user.email "email_id"` | Configure  User Email |
| `git config -- user.name "your_name"` | Configure  User Name |

<br>

## Branches

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (The asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |



## Setup *
#### 
`git config -- user.email "email_id"` <br>
`git config -- user.name "your_name"`

<br>

## Branches
#### Show all branches
 `git branch`
 
#### Checkout or switch to an existing branch
`git checkout <branch_name>`

#### Create & checkout branch (copies from current checked-out branch)
   `git checkout -b <branch_name>`
   
#### new branch naming conventions 
 **For new feature:**  `git checkout -b <feature/name>` <br>
 **For new bugfix:**  `git checkout -b <bugfix/name>` <br>
 **For new hotfix:**  `git checkout -b <hotfix/name>`
   
#### Create & checkout branch (copies from specific branch)
   `git checkout -b <new_branch_name> <existing_branch_name>`
 
#### Delete a branch
  ` git branch --delete <branch_name> `

<br>

## Merge *
#### Merge files to the main branch
**Change to main branch** <br>
  ` git checkout main `

**Merge files** <br>
  ` git merge <branch_name> `

<br> 

## Commit
#### Add files
  **Add all files** <br>
 ` git add . ` <br>
 
  **Add specific files** <br>
   ` git add <file_name1, file_name2, etc> ` <br>
 Note: Must add files before commit
 
#### Commit the Added files
` git commit -m 'info_message' `

<br>

## Push *
#### Push to origin
**Push a branch to remote repository** <br>
` git push <variable name ex:origin> <branch_name> `
  
**Push all branches, This command pushes all branches to your remote repository.** <br>
` git push -all <variable name ex:origin> `

<br>

## Pull *
#### Pull from remote repository 
` git pull [repository link] `

#### Pull all changes 
` git pull `

<br>

## Rebase *

<br> 

## Maven
#### Build package
` mvn clean package `

<br> 


## MISC
#### List
To show all files from current location <br>
` ls -la `


#### Remove Files
To remove files, folders from current location <br>
` rm -rf <branch_name1, branch_name2, branch_name1> `
