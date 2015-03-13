# Functional Specification Document

## Project Core Team
* [Eric Chu](https://github.com/ericchu94)
* [Weiping (Allen) Hsiao](https://github.com/allenh)
* [Rui Sun](https://github.com/r29sun)
* [Dennis Zhang](https://github.com/FlipEnergy)

## Introduction

### Purpose
The purpose of this document, Functional Specification Document (abbreviated as FSD hereafter), is to outline the functional specifications for the project based on the requirements outlined in the Business Requirement Document (abbreviated as BRD hereafter) under modules.

### Module References
Modules in this document refer to the modules described in the BRD and address the functional specification for the system with respect to that module.

### User Interface Description
A high level description outlining the user interface following the functional specifications for the corresponding module.

### Data Format
All data transmitted between the client and server through the websocket is in JSON unless otherwise specified.

## Modules
### Module 1 - Initiation
#### User Interface Description
* Display messages view
  * This view needs to be populated with the latest 10 messages, with a control at the top to load previous messages, and scrolled to bottom initially
* Type message control
* Submit message control

#### Events
* If and only if there is only white space in the message control, disable the submit control
* When Enter is pressed in the message control, simulate a click on submit control
* When the submit control is clicked, and if there is not only white space in the message control, and if there is not already a message post in progress, send the text in the message control to the server using a websocket post
* When the server responds from a message post, and if there is no error, focus and clear the message text
* When the server receives a message via post, and if the message text is not only white space, attach a timestamp (milliseconds since unix epoch) to the message, broadcast it to all connected websockets, and respond to the post indicating success
* When the client receives a message from the websocket, display it in the messages view, and if the messages view was originally scrolled to the bottom, scroll to the bottom again
* When the previous messages control is clicked, disable the control, and send a websocket get with the timestamp of the first message
* When the server receives a load previous messages request via get, send (up to) 10 messages most recently prior to the timestamp to the client
* When the client receives the previous messages, enable the previous messages control, and display the messages in the messages view

### Module 2 - Authentication
#### User Interface Description
* Display messages view
  * Messages include a username control
* Sign Up view
  * Email control
  * Password control
  * Confirm password control
  * Username control
  * Output message control
  * Submit control
* User management view
  * Change email control
  * Change password control
  * Confirm change password control
  * Change username control
  * Output message control
  * Submit control
* Login view
  * Email control
  * Password control
  * Remember me control
  * Output message control
  * Submit control

#### Events
##### Chat room
* When loading the chat room, show login view if user is not logged in
* When the server receives a message via post, and if the message text is not only white space, attach a timestamp (milliseconds since unix epoch) to the message, attach the username associated with the message, broadcast it to all connected websockets, and respond to the post indicating success

##### Sign up
* Pressing Enter in any input control in the sign up view will change focus to the next input control, unless the control is a submit control
  * If the next control is a submit control, simulate a click on the control
* If and only if any fields are empty in the sign up view, disable the submit control
* When the Sign up view's submit control is clicked, if it is active, and a sign up request is not already in progress, validate that password and confirm password is the same, and if not, display an error message
  * If the passwords are the same, send a sign up request via websocket post
* When the server receives a sign up request, validate that the username and email fields are unique, and if not, respond with an error message
  * If the validation is successful, create the user, and log in, and respond indicating success
* When the client receives the response to the sign up request, display the error message if unsuccessful, otherwise, show the chat room

##### User management
* Pressing Enter in any input control in the user management view will change focus to the next input control, unless the control is a submit control
  * If the next control is a submit control, simulate a click on the control
* When the User management view's submit control is clicked, and an user update request is not already in progress, validate that password and confirm password is the same, and if not, display an error message
  * If the passwords are the same, send a user update request updating all non-blank fields
* When the server receives a user update request, validate that the username and email fields are unique, and if not, respond with an error message
  * If the validation is successful, update the fields, and respond indicating success
* When the client receives the response to the sign up request, display the error message if unsuccessful, otherwise, display a success message

##### Login
* Pressing Enter in any input control in the login view will change focus to the next input control, unless the control is a submit control
* If and only if any fields are empty in the login view, disable the submit control
* When the Login view's submit control is clicked, if it is active, and a log in request is not already in progress, send a log in request via websocket post
* When the server receives a sign up request, validate that the email and password fields correspond to a user, and if not, respond with an error message
  * If the validation is successful, log in and set session expiration time, and respond indicating success
* When the client receives the response to the log in request, display the error message if unsuccessful, otherwise, show the chat room

### Module 3 - Contact List
#### User Interface Description
* Status control
  * Online
  * Offline
  * Away
  * Busy
* Add contact control
* Output message control
* Contact list view
  * Favorites list view
    * Populated with favorited contacts
    * Contact list item view
  * Normal contacts list view
    * Populated with all contacts
    * Contact list item view
  * Contact list item view
    * Status control
    * Name control
    * Contact context menu control
      * Add/remove favorite control
      * Add/remove contact control

#### Events
* When a user logs in, broadcast the user's status to all users that have the user in contacts
* When a user logs out, broadcast the user's status as offline to all users that have the user in contacts
* When a user changes status, broadcast the user's status to all users that have the user in contacts
* Pressing any key in the add contact control clears the output message
* Pressing enter in the add contact control, and if the control is not all whitespace, sends an add contact request via websocket post
* When the server receives an add contact request, validate that the user exists, and that the contact is not already added, and if not, respond with an error
  * If successful, add the contact and respond indicating success with contact status
* When the client receives an add contact response, if success, clear the add contact control, add the new contact with status, focus the new contact, and output a success message
  * If failed, output the error
* When a contact or an user is right-clicked on, display the custom context menu
  * The favorite control depends on whether the user is already favorited
  * The contact control depends on whether the contact is already added
* When the context menu's action control is clicked, send the respective request using a user's id (instead of username) via websocket post, and close the context menu
* when the server receives a remove contact request, validate that the contact exists and is in the contact list, remove the contact, and send a message indicating success or failure
* When the server receives a add/remove favorite request, validate that the contact exists and is in the contact list, add/remove the favorite, and send a message indicating success or failure

### Module 4 - User-based Chatting System
1. The system shall only create a chat room if there are two or more users for the chat room
2. The system shall allow users to belong in more than one chat rooms simultaneously
3. The system shall not allow a new chat room to be created if the chat room with the same users already existed
4. The system shall allow any user to initiate a chat room with one (one-to-one chat room) or more users (group chat room) without violating the third point under Module 4
5. The system shall allow all the participants in a chat room to view the history of the chat
6. The system shall preserve all the chat instances that a user belongs and allow them to return to those chat rooms after they re-log into the system
7. The system shall allow any user who belongs in a chat room to leave at anytime
8. The system shall allow the user who left the chat to be able to view the chat history to the point that they left the chat room
9. The system shall allow the users to rename any chat instance that they belong to

	#### User Interface Description
	* Right Click On anyone or the group the user has in their contact list:
		* Initiate (create) chat room
		* Remove User
			* When this action is performed in a group then the user will proceed to select which user(s) to remove from that particular group

### Module 5 - Adding/Removing participant to existing chat instances
1. The system shall allow anyone who participates in a chat room to add any other user who is not already participating in the same chat room on their contact list to join the chat room

	a.  If the chat room is one-on-one then the person who invites the new user will become the creator to that chat room
2. The system shall allow the creator of a group chat to remove any user within the group chat without being restricted by Module 4 third point
3. The system shall allow the user to add user to their group chat without being restricted by Module 4 third point
