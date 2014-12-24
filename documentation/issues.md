# GitHub issues

## Viewing issues
* When viewing the repository, the second tab on the right hand side is the [issues] (https://github.com/ericchu94/chat/issues).

## States
* Each issues has 2 possible states: open, and closed
* A issue should be closed only after it is completely done
* A issue can be reopened if it is not finished

## Assignees
* Each issue can be assigned to at most 1 person
* The person that is assigned should be the person that is to work on the issue

## Milestones
* Milestones are a great way to categorize issues
  * For example: core functionality, nice to have, etc.
* An issue does not need to have a milestone

## Labels
* All issues should have 1 label that is not review
* A issue may also have the review label, when the issue is to be reviewed

## Reviews
* When an issue is to be reviewed, the review label should be added
* The issue should then be assigned to the reviewer
* The reviewer should look at the issue and comment on whether the issue is finished or not
* The reviewer then assigns the issue back to the initial assignee, and removes the review label
* Tips
  * To view all changes of a branch try ```git diff master...gh-3```

## Lifecycle
A standard issue has the following lifecycle:
 1. Issue is created
 2. Labels, milestones and assignee are added
 3. Assignee works on the issue
 4. Assignee sets the review label, and assigns issue to creator
 5. Creator reviews issue, comments, removes review label, and assigns back to asignee
 6. Assignee loops back to 3. if creator does not accept solution
 7. Assignee closes the issue
