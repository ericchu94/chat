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
  * A timestamp must be displayed for each message
  * Messages are seen by all users, including previous messages

### Module 2 - Authentication
* Users are required to sign up with username, password and email
  * usernames must be unique
    * If users input a taken username, a message will tell them so
  * emails must be unique
    * If users input a taken email, a message will tell them so
  * Option to change Username
    * Username can only be changed once every 4 months (3 times a year), counting begins upon account creation
    * If users try to change their username while they are not allowed, a message will tell them how much longer they need to wait before they are allowed to change their username again.
  * Option to change Password
  * Option to change email
    * If users input a taken email, a message will tell them so
* Users are required to log in with said username and password to join chat room
  * Allow "remember me" for quick sign in
  * log in page will also have a "Forgot Password" button that will send a password reset link to an inputted email
    * If inputted email is not registered, a message will tell them so 
    * If reset email was successfully sent, a message will tell them so
* Username preface every message to indicate who sent the text

### Module 3 - Contact lists 
* Users will each have a contact list
  * Add/remove users from contact list
  * Favorites list within contact list
  * display contact's online status
  * choose how to display your online status (online, away, busy, etc.)

### Module 4 - User-based Chatting System
* No longer one large chat room
* Chat instances are based on the users who are in them and only chats between two or more contacts can be created
 * Each chat instance can be one of two types: group or one-on-one
   * Chat instances cannot change from one to another
    * Chat instances with only two participants upon creation are one-on-one
    * Chat instances with three or more participants upon creation are group chats
      * Even if participants leave and the chat ends up with two participants, the instance is still considered a group chat
      * All messages sent by each participant in this group chat can be seen by every other participant.
      * Each participant can review the history of the group chat if they did not leave
 * Users can be in more than one instance at a time
 * If a chat instance exists between a combination of users, a new instance of the same combination cannot be created
   * Note: Existing instances can be modified to end up with the same combination of users as another existing instance
    * Example: A, B, C, and D are chatting in instance *one*, another instance with exactly A, B, C, and D cannot be created. If A, B, and C creates a new chat instance, *two*, and then D leaves instance *one*, instances *one* and *two* would still both exist.
 * A user can choose a new group of contacts or a single contact to start a new chat instance
  	* User can directly select a contact to chat one-one-one
   	* User can also first create a group chat, then select the participants from their contact list, then send messages to all of them. 
   	  * If user selected only one contact, then either the existing one-on-one chat is opened (if it exists) or a new one-on-one chat is created.
   	  * If user selected a group that already has one or more existing group chat instances, then the most recent one is to be opened.
* Users can return to existing chat instances after re-logging in
  * There needs to be way for them to browse existing instances they are already chatting in
* Old messages can be seen, including those sent while user is offline
 * Users can still leave messages if no one that they are chatting with is online
* Users can leave a group chat at anytime
  * The rest of the participants can still chat and will see indication saying "X has left the group chat."
  * If users leave, a message will show up stating that they have left the group chat
  * A user can still review the group chat history up until the point of when they leave after they leave
    * If the number of participants reach one, then that last participant will not be able to send any more messages, but they can still view the chat history
  * If all participants leave the group chat, then the group chat instance wll be removed
* The user who creates a group chat can name and rename the group chat instance.
 * Note: Only applies to group chat instances. One-on-one chats will just display the username of the other person the user is chatting with.

### Module 5 - Adding/removing participants to existing chat instances
* A user can add multiple contacts at once to an existing chat instance at any time
 * If old instance is already a group chat, newly added users can still see previously sent messages by old users
 * If old instance is one-on-one, then a new instance will be created and the user who added the new participant is considered the creator of the group chat
 * Note: Just as in module 4, existing instances can be modified to end up with the same combination of users as another existing instance
 * Example: A, B, and C are chatting in instance *one*, another instance with exactly A, B, and C cannot be created. If A, B, C, and D creates a new chat instance, *two*, and then D is added to instance *one*, instances *one* and *two* would still both exist.
 * The group chat creator can remove participants from a group at any time
   * The removed particiant will see a message stating they have been removed
    * All other participants will see indication saying "X has been removed from the group chat."
