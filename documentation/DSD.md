# Functional Specification Document

## Project Core Team
* [Eric Chu](https://github.com/ericchu94)
* [Weiping (Allen) Hsiao](https://github.com/allenh)
* [Rui Sun](https://github.com/r29sun)
* [Dennis Zhang](https://github.com/FlipEnergy)

## Introduction

### Purpose
The purpose of this document, Design Specification Document (abbreviated as DSD hereafter), is to outline the design specifications for the project based on the requirements outlined in the Functional Specification Document (abbreviated as FSD hereafter) under modules.

### Module References
Modules in this document refer to the modules described in the FSD and address the design specification for the system with respect to that module.

## Modules
### Module 1 - Initiation
* Display messages view
  * Display messages view is initially empty.
  * This view will be populated with at most 10 messages and will be scrolled down to the bottom.
  *	The load previous messages control will appear at the top of display messages view. 
  *	If the very first message is displayed in the display messages view, the load previous messages control will be disabled.
* Type messages control
  *	Type messages control should be under the display messages view.
  *	Input will be displayed in type messages control before it is submitted.
* Submit messages control
  *	The submit messages control should be under the right corner of type messages control.
  *	 The submit control will be of color grey indicating it’s disabled if the type messages control is empty. Otherwise it should be white.

