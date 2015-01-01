# Business Requirements Document

## Project Core Team
* [Eric Chu](https://github.com/ericchu94)
* [Weiping (Allen) Hsiao](https://github.com/allenh)
* [Rui Sun](https://github.com/r29sun)
* [Dennis Zhang](https://github.com/FlipEnergy)

## Introduction

### Purpose
Our goal is to create a web-based chatting system that will allow users to send text messages in real time. The final product should resemble messengers like Skype, WeChat and Facebook chat, etc.

### Scope
The scope of the project is not set in stone as the team will learn and gain more ways to contribute as the project moves foward. Hence, we will break the project up into modules in which we will specify goals for improvement and enhancement.

### What are Modules?
Modules are phases in the project and will underline the goals of that phase. All goals in a module state what the project will be able to do upon completion. Modules are to be completed in order.

## Methodology
The system will be written in node.js using the sails.js framework. Tasks will be initiated by issues then assigned to one of project team members who will then work on the issue on a remote branch. When the task is deemed done by all members of the team, it will then be merged to the master branch in the repository. For more details, refer to [git.md](https://github.com/ericchu94/chat/blob/master/documentation/git.md) and [issues.md](https://github.com/ericchu94/chat/blob/master/documentation/issues.md).

## Modules

### Module 1 - Initiation
* Create a single chat room where users can chat with other users in realtime
  * Messages are text only
  * Messages are displayed in chonological order
  * Messages are seen by all users, including previous messages

### Module 2 - Authentication
* Users are required to sign up with username, password and email
  * Option to change Username
  * Option to change Password
  * Option to change email
* Users are required to log in with said username and password to join chat room
  * Allow "remember me" for quick sign in

### Module 3 - Contact lists 
* Users will each have a contact list
  * Add/remove users from contact list
  * Favorites list within contact list
  * display contact's online status
  * choose how to display your online status (online, away, busy, etc.)

### Module 4 - User-based Chatting System
* No longer one large chat room
* Chat instances are based on the users who are in them and only chats between two or more contacts can be created
 * Users can be in more than one instance at a time
 * Multiple chat instances between the same combination of users are not allowed
 * A user can choose a new group of contacts or a single contact to start a new chat instance
  	* User can directly select a contact to chat one-one-one
   	* User can also make a new message and select who, from their contacts, to send it to, creating a group chat
 * Users can return to existing chat instances after re-logging in
  * Old messages can be seen, including those sent while user is offline
  * Users can still leave messages if no one that they are chatting with is online
 * Users can leave a group chat at anytime

### Module 5 - Adding Contacts to existing chat instances
* A user can add multiple contacts at once to an existing chat instance at any time
 * If old instance is already a group chat, newly added users can still see previously sent messages by old users
 * If old instance is one-on-one, then a new instance will be created
