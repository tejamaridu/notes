 
# GIT
 
## <span style="color: blue;">Setup</span> 
### Setup User Email, Name
`git config -- user.email "email_id"` <br>
`git config -- user.name "your_name"`

<br><br>

## Branches
### Show all branchs
 `git branch`
 
### Create a new branch 
  `git branch <feature/name>` <br>
  `git branch <bugfix/name>` <br>
  `git branch <hotfix/name>`

### Create & Checkout Branch at one time
   `git checkout -b  <feature/name>`

### Switch to existing branch
`git checkout <branch_name>`

<br><br>

## Commit
### Add files
  **Add all files** <br>
 ` git add . ` <br>
 
  **Add specific files** <br>
   ` git add <file_name1, file_name2, etc> ` <br>
 Note: Must add files before commit
 
### Commit the Added files
` git commit -m 'info_message' `

<br><br>

## Merge
### Merge files to main branch
**Change to main branch** <br>
  ` git checkout main `

**Merge files** <br>
  ` git merge <branch_name> `

<br><br>

## Push
### Push to origin
**Push a branch to remote repository** <br>
` git push <variable name ex:origin> <branch_name> `
  
**Push all branches, This command pushes all branches to your remote repository.** <br>
` git push -all <variable name ex:origin> `

### Push to remote repository 
` git pull [repository link] `

<br><br>

## MISC
### List
To show all files from current location <br>
` ls -la `
