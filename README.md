# A Heroes Journey
52685 Working with Data and Code

Assessment 2 Final Project

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
(<img width="1470" alt="Screenshot 2024-11-01 at 9 52 25 pm" src="https://github.com/user-attachments/assets/fad26c13-78c8-4d07-94f0-d5d529bc5082">)
<!-- If you have screenshots you'd like to share, include them here. -->


## Setup
[_A Heroes Journey_](https://makecode.com/_8p6FyJT9999g)


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
controller.up.on_event(ControllerButtonEvent.PRESSED, on_up_pressed)
def on_button_released():
    animation.stop_animation(animation.AnimationTypes.ALL, mySprite)
controller.any_button.on_event(ControllerButtonEvent.RELEASED, on_button_released)`

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

_Code Example (Level 2)_ 
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
- Improvement to be done 1
- Improvement to be done 2

To do:
- Feature to be added 1
- Feature to be added 2


## Acknowledgements
Give credit here.
- This project was inspired by...
- This project was based on [this tutorial](https://www.example.com).
- Many thanks to...


## Contact
Created by Nathan Ngo (13777406)


<!-- Optional -->
<!-- ## License -->
<!-- This project is open source and available under the [... License](). -->

<!-- You don't have to include all sections - just the one's relevant to your project -->
