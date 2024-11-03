# A Heroes Journey
52685 Working with Data and Code

Assessment 2 Final Project

Game Link [_A Heroes Journey_](https://makecode.com/_8p6FyJT9999g)

> Explainer Video [_here_](https://www.example.com)


## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Features](#features)
* [Screenshots](#screenshots)
* [Setup](#setup)
* [Usage](#usage)
* [Project Status](#project-status)
* [Room for Improvement](#room-for-improvement)
* [Acknowledgements](#acknowledgements)
* [Contact](#contact)
<!-- * [License](#license) -->


## General Information
The project I have undertaken for A2 is creating a video game on Microsoft MakeCode Arcade. The aim of my project was to create an engaging game that can be easily picked up by anyone. The reason I chose to code a game is because I do enjoy playing them however, I never thought I'd have the opportunity to ever create one as coding in general never interested me. In doing this subject it allows me to explore what goes behind video game coding and gives me the tools and resources to go and create a simple game. 

The game so far consists of two levels. The first level showcases a maze where the player goes around and finds objects, the second level consists of monsters where the player has to take them down. 

## Technologies Used
- Tech 1 - version 1.0
- Tech 2 - version 2.0
- Tech 3 - version 3.0


## Features
List the ready features here:
- Awesome feature 1
- Awesome feature 2
- Awesome feature 3


## Screenshots

### Game Title

<img width="1470" alt="Screenshot 2024-11-01 at 9 52 25 pm" src="https://github.com/user-attachments/assets/fad26c13-78c8-4d07-94f0-d5d529bc5082">

### Errors that occured

Character showing uop in different locations 

<img width="1463" alt="Screenshot 2024-10-25 at 12 10 59 pm" src="https://github.com/user-attachments/assets/8d400d8e-969c-43d3-9c69-0ba9a9dcc545">

Level map changing when overlapping objectives

<img width="1470" alt="Screenshot 2024-11-03 at 3 35 24 pm" src="https://github.com/user-attachments/assets/654686da-cc2f-4eae-8c20-fab848dd3fb4">

Projectiles only firing in one directon

<img width="1463" alt="Screenshot 2024-10-25 at 12 10 59 pm" src="https://github.com/user-attachments/assets/71eee8e6-4f12-4c5b-bded-51f8dbc9a69d">

## Setup
This project is accessible in two ways.

First Way (using URl)
1. Open Microsoft MakecodeArcade and create an account if you don't have one
2. Copy this URL 

Second Way (opening via Microsoft Makecode Arcade)
1. Open Microsoft MakecodeArcade and create an account if you don't have one
2. Download this [image](https://github.com/user-attachments/assets/252435ee-c131-49b7-a5ed-e8e85905631e)
4. Navigate to 'Import Files' and import the image
5. Click 'Go ahead!' and the game should be accessible

[First Iteration](https://arcade.makecode.com/S87170-49744-88411-08192)


[Final Version]


What are the project requirements/dependencies? Where are they listed? A requirements.txt or a Pipfile.lock file perhaps? Where is it located?

Proceed to describe how to install / setup one's local environment / get started with the project.


## Usage
When the game first starts the player is introduced to the first character then are placed in the first level. 
Players move the character by pressing (up, down, left, right) or (W,A,S,D) 

_Code Example (Movement)_ 

`def on_up_pressed():
    animation.run_image_animation(mySprite, assets.animation("""
        Move Up
    """), 200, True)
controller.up.on_event(ControllerButtonEvent.PRESSED, on_up_pressed)`

When players navigate the maze there come across different objects (chests, characters). When the player comes across these objects a brief message will appear and the score will go up by one. 

_Code Example (Overlapping)_ 

`def on_overlap_tile5(sprite6, location6):
    info.change_score_by(1)
    game.show_long_text("You have found a \"Ruby Ring\"", DialogLayout.BOTTOM)
    tiles.set_tile_at(location6, assets.tile("""
        Open Red
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Red Chest
    """),
    on_overlap_tile5)`

When all artefacts are found the player will make their way to a portal to enter the next level of the game. This level the player fires projectiles at enemies before the countdown ends to win

_Code Example (Projectiles)_ 

`def on_a_pressed():
    global projectile2
    direction = 0
    if direction == 0:
        projectile2 = sprites.create_projectile_from_sprite(img("""
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . 5 5 5 5 5 5 5 5 . . . .
            . . . . 5 5 5 5 5 5 5 5 . . . .
            . . . . 5 5 5 5 5 5 5 5 . . . .
            . . . . 5 5 5 5 5 5 5 5 . . . .
            . . . . 5 5 5 5 5 5 5 5 . . . .
            . . . . 5 5 5 5 5 5 5 5 . . . .
            . . . . 5 5 5 5 5 5 5 5 . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
            . . . . . . . . . . . . . . . .
        """),
            mySprite,
            50,
            0)
controller.A.on_event(ControllerButtonEvent.PRESSED, on_a_pressed)
def on_countdown_end():
    game.game_over(False)
info.on_countdown_end(on_countdown_end)`

## Project Status
Project is: _in progress_

## Room for Improvement
Include areas you believe need improvement / could be improved. Also add TODOs for future development.

Room for improvement:
- Allowing projectiles to fire in different directions depending on where the character is pointing at
- 

To do:
- Allowing enemies to be taken down by projectiles
- Adding music and sound effects to the game


## Acknowledgements
Give credit here.
- This project was inspired by games (Pokemon, The Legend of Zelda), Guides ([80's Rockstar Maze](https://arcade.makecode.com/--skillmap#rockstar))
- This project was based on [Tutorial 5 Computer History and Introduction to Microsoft Makdecode Arcade](https://canvas.uts.edu.au/courses/33108/files/8081046?module_item_id=2021301).

## Contact
Created by Nathan Ngo (13777406)


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
