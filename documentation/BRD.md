# Business Requirements Document
Version 1 --- Author: Dennis Zhang --- December 30, 2014

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
Modules are phases in the project and will underline the goals of that phase. All goals in a module state what the project will be able to do upon completing the module. Modules are to be completed in order.

## Methodology
The system will be written in node.js using the sails.js framework. Tasks will be initiated by issues then assigned to one of project team members who will then work on the issue on a remote branch. When the task is deemed done by all members of the team, it will then be merged to the master branch in the repository. For more details, refer to [git.md](https://github.com/ericchu94/chat/blob/master/documentation/git.md) and [issues.md](https://github.com/ericchu94/chat/blob/master/documentation/issues.md).

## Modules

### Module 1 - Initiation
* Create a single chatroom where users can chat with other users in realtime
  * Messages are only text
  * Messages are displayed in chonological order
  * Messages are seen by all users, but only ones sent after they've joined

### Module 2 - Enhancing User experience
* Allow users to assign usernames to themselves
  * Messages are prefaced by username
* Multiple (a set number of) chatrooms that users are join
  * Chatrooms should specify users in them
  * Users are free to leave and re-enter chatrooms
  * Users can be in more than one chatroom at a time

### Module 3 - Authentication
* Users are required to sign up with username, password and email
  * Option to change Username
  * Option to change Password
  * Option to change email
* Users are required to log in with said username and password
  * Allow "remember me" for quick sign in

### Module 4 - Contact lists
* Users will each have a contact list
  * Add/modify/remove friends from contact list
  * join the room the contact is in from contact list
  * Users can invite contacts from contact list to join the room they're in

### Module 5 - Room Creation
* chatrooms are able to be created
  * If a chatroom consisting of a group of users already exists, users can rejoin chatroom after signing off
  * If a chatroom consisting of a group of users does not yet exist, a new chatroom is created
  * Users can see previously sent messages in the room
