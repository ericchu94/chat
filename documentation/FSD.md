# Functional Specification Document

## Project Core Team
* [Eric Chu](https://github.com/ericchu94)
* [Weiping (Allen) Hsiao](https://github.com/allenh)
* [Rui Sun](https://github.com/r29sun)
* [Dennis Zhang](https://github.com/FlipEnergy)

## Introduction

### Purpose
Outline the functional specifications for the project based on the requirements outlined in the Business Requirement Document (BRD).

### What are modules used in this document
Modules in this document refer to the modules described in the BRD and address the functional specification for the system with respect to that module.

## Modules
### Module 2 - Authentication
1. The system shall allow the users to log-in to the system.
2. The system shall allow the users to sign-up for the system.

### System Interface Description

* The user will first arrive at a log-in page where there are two textboxes and two buttons.
* The first textbox allows the user to enter their registered username and the second textbox allows the user to enter the corresponding password.
* The first button, says "Submit", will validate the supplied credentials by the user against the system's database.
* The second button, says "Sign Up", will redirect the user to the sign-up page where it allows the user to sign up for the system
* The sign-up page consists of 3 lines of texts, 3 textboxes and 1 button:
	*  Text: username, password, display name
	*  Textbox: each textbox is for the user to enter their desired username, password and display name
	*  Button: allows the user to submit information
*  Note: During each phase the user has to fill-in all the textboxes before they can click the submit button.