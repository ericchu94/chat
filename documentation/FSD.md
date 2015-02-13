# Functional Specification Document

## Project Core Team
* [Eric Chu](https://github.com/ericchu94)
* [Weiping (Allen) Hsiao](https://github.com/allenh)
* [Rui Sun](https://github.com/r29sun)
* [Dennis Zhang](https://github.com/FlipEnergy)

## Introduction

### Purpose
The purpose of this document, Functional Specification Document (abbreviated as FSD hereafter), is to outline the functional specifications for the project based on the requirements outlined in the Business Requirement Document (abbreviated as BRD hereafter) under modules.

### What are modules used in this document
Modules in this document refer to the modules described in the BRD and address the functional specification for the system with respect to that module.

### User Interface Description
A high level description outlining the user interface following the functional specifications for the corresponding module.

### Document Reference
When referencing document in this document only those referencing BRD will be explicitly stated.

## Modules
### Module 1 - Initiation
1. The system shall allow the users to create a chat room in realtime with contacts in contact list (as defined in Module 3 in BRD).
2. The system shall associate each message with a timestamp at the time the message is sent in terms of the server time.
3. The system shall store the prior messages (parts of chat history) in most recent first ordering within the chat room is chornological order following the timestamp of the message given under the second point.

	#### User Interface Description
	* The window will be split into two portions. First half is for displaying the prior messages and the other half has a textbox where it allows the users to enter text only messages and a button where it allows the user to send the messages entered in the textbox
		* The users can also hit the Enter/Return key to send the message
	* The timestamp for each message is displayed with it's corresponding message in 24-hour time
	* There will be a button that allows the user to click in order to leave the chat room

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
	* A dropdown menu beside each contact to perform additional functions such as start chat, add to faviourite or remove
	* A button that add users by their username
	* A dropdown menu of status to choose from to indicate your online status
	* A separate list that displays a list of contacts indicated by the user as their faviourites

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