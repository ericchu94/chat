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
1. The system shall allow the users to log-in to the system.
2. The system shall allow the users to sign-up for the system.

	#### User Interface Description
	* The user will first arrive at a log-in page where there are two textboxes and two buttons.
	* The first textbox allows the user to enter their registered username and the second textbox allows the user to enter the corresponding password.
	* The first button, says "Submit", will validate the supplied credentials by the user against the system's database.
	* The second button, says "Sign Up", will redirect the user to the sign-up page where it allows the user to sign up for the system
	* The sign-up page consists of 3 lines of texts, 3 textboxes and 1 button:
		*  Text: username, password, display name
		*  Textbox: each textbox is for the user to enter their desired username, password and display name
		*  Button: allows the user to submit information
	*  Note: During each phase the user has to fill-in all the textboxes before they can click the submit button.

### Module 3 - Contact List
1. The system shall have a window that displays each user's contacts

	#### User Interface Description
	* A list that displays all the contact and their online online status (colour indication)
	* A dropdown menu beside each contact to perform additional functions such as start chat, add to favorite or remove
	* A button that add users by their username
	* A dropdown menu of status to choose from to indicate your online status
	* A separate list that displays a list of contacts indicated by the user as their favorite

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
