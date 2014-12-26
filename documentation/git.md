# Git workflow

## Setup
* Ensure that the name and email matches with information from the github account

## Git clone
* The ```git clone``` command typically needs to be run only once
* This command creates a copy of the repository and also adds a remote called origin
  * The remote is used for pulling and pushing

## Tackling issues
The workflow for resolving issues involving the repository is as follows:
 1. Create a feature branch to work on the issue
    * ```git checkout master```
    * ```git checkout -b gh-7```
 2. Make changes to the repository
 3. Add and commit these changes
    * ```git add```
    * ```git commit```
      * Make sure the commit message is correct
        * The first line should be a summary of the commit (eg: Added name fields to user model)
        * The second line should be blank
        * The next few lines should be details of the commit
          * (eg: Added first name field)
          * (eg: Added last name field)
        * The last line should be a issue reference (eg: gh-7)
 4. Push the feature branch to github
    * ```git push origin gh-7```
 5. Pass the code review
 6. Update the local branches using ```git pull```
 7. Merge the feature branch into master
    * ```git checkout master```
    * ```git merge gh-4```
 8. Push the changes to the tracking branch
    * ```git push```
