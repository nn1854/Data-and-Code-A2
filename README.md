# 52685 Working with Data and Code

### Assessment 2 Final Project - A Heroes Journey

> Explainer Video [_here_](https://www.example.com)

> Reflection [_here_](https://www.example.com)


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
- Microsoft MakeCode Python

## Features
- Retro style arcade game
- 2 different levels (level 2 in progress)
- Points system
- Countdown timer
- Player controls 

## Screenshots

### Game Title

<img width="1470" alt="Title" src="https://github.com/user-attachments/assets/3002abe4-f799-45b3-a56b-80a8faea21ab">

### Game Map

<img width="700" alt="Level 1 tilemap" src="https://github.com/user-attachments/assets/e997cb38-0773-4c9e-b3be-c984d6b1f183">


### Errors that occured

Character showing up in different locations 

<img width="1463" alt="Player in multiple locations" src="https://github.com/user-attachments/assets/53d9ce76-1676-4fe7-b073-584ef3967e85">

Level map changing when overlapping objectives

<img width="1470" alt="Player going though walls" src="https://github.com/user-attachments/assets/139131c6-1580-460f-8665-7f9ec126959b">

Projectiles only firing in one directon

<img width="1464" alt="Projectile in one direction" src="https://github.com/user-attachments/assets/138c44a9-acfe-4966-a741-3e0061ed80d0">
<img width="1466" alt="Projectile up" src="https://github.com/user-attachments/assets/c3c45136-5f56-47ab-b5eb-ec765abce59f">

## Setup
This project is accessible in two ways.

First Way (using URL)
1. Click on this URL https://makecode.com/_AYqXLu5uqR8q or open it in a new tab
2. The game should now be accessible 

Second Way (opening via Microsoft Makecode Arcade)
1. Open Microsoft MakecodeArcade and create an account if you don't have one
2. Download this [image](https://github.com/user-attachments/assets/d05cd339-a59e-403b-873b-50dda3ed60b6)
4. Navigate to 'Import Files' and import the image
5. Click 'Go ahead!' and the game should be accessible

> First iteration of game [_here_](https://arcade.makecode.com/S87170-49744-88411-08192)

## Usage

When the game first starts the player is introduced to the first character then are placed in the first level.

> _Game Start Code_

`@namespace
class SpriteKind:
    NPC = SpriteKind.create()
    Warrior = SpriteKind.create()
projectile2: Sprite = None
mySprite: Sprite = None
Wizard: Sprite = None
level = 0
game.splash("A Heroes Journey")
level = 1
Wizard = sprites.create(assets.image("""
    Wizard
"""), SpriteKind.NPC)
game.show_long_text("Good Morning, Sorry to disturb you.", DialogLayout.BOTTOM)
game.show_long_text("My name is Morley and I am a what you'd call a wizard of sorts.",
    DialogLayout.BOTTOM)
game.show_long_text("Lucky I found you, I am in need of your urgent assistance.",
    DialogLayout.BOTTOM)
game.show_long_text("There is are monsters terrorising the kingdom and I need you to slay them. ",
    DialogLayout.BOTTOM)
game.show_long_text("You need to find 6 artefacts scattered across the forest then find the blue portal. ",
    DialogLayout.BOTTOM)
game.show_long_text("Good Luck Hero, We are counting on you!!",
    DialogLayout.BOTTOM)
startLevel()`

Players move the character by pressing (up, down, left, right) or (W,A,S,D) 

> _Code Example (Movement)_ 

`def on_up_pressed():
    animation.run_image_animation(mySprite, assets.animation("""
        Move Up
    """), 200, True)
controller.up.on_event(ControllerButtonEvent.PRESSED, on_up_pressed)`

When players navigate the maze there come across different objects (chests, characters). When the player comes across these objects a brief message will appear and the score will go up by one. 

> _Code Example (Overlapping)_ 

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
    
> _(Overlapping Monster for minigame)_

`def on_overlap_tile10(sprite3, location3):
    game.show_long_text("You can't pass until you defeat the monsters",
        DialogLayout.BOTTOM)
    tiles.set_tile_at(location3, assets.tile("""
        Monster 2
    """))
    clearLevel()
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Monster
    """),
    on_overlap_tile10)`

> _Code Example (Level Design)_

`def createLevel():
    if level == 1:
        tiles.set_current_tilemap(tilemap("""
            Level 1
        """))
    elif level == 2:
        game.show_long_text("Goodluck hero, we are all counting on you",
            DialogLayout.CENTER)
        level2()
    else:
        tiles.set_current_tilemap(tilemap("""
            Level 1
        """))
        scene.set_background_color(7)
        info.stop_countdown()
    controller.move_sprite(mySprite)
    tiles.place_on_random_tile(mySprite, sprites.castle.tile_path5)
    scene.camera_follow_sprite(mySprite)`

When all artefacts are found the player will make their way to a portal to enter the next level of the game. This level the player fires projectiles (A button) at enemies before the countdown ends to win.

> _Code Example (Projectiles)_ 

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
    game.game_over(False)`

> _Code Example (Sprite and Enemey)_

`def startLevel():
    global mySprite, monster
    sprites.destroy(Wizard)
    scene.set_background_color(7)
    tiles.set_current_tilemap(tilemap("""
        Level 1
    """))
    mySprite = sprites.create(assets.image("""
        Hero
    """), SpriteKind.player)
    controller.move_sprite(mySprite)
    tiles.place_on_random_tile(mySprite, sprites.castle.tile_path5)
    scene.camera_follow_sprite(mySprite)
    monster = sprites.create(assets.image("""
        Hero
    """), SpriteKind.enemy)
    tiles.place_on_random_tile(monster, sprites.castle.tile_grass3)
    monster.set_velocity(50, 50)
    monster.set_bounce_on_wall(True)
    monster.follow(mySprite, 75)
    createLevel()`

## Project Status
Project is: _in progress_

## Room for Improvement

Room for improvement:
- Allowing projectiles to fire in different directions depending on where the character is pointing at
- Player character continuosly moving rather than being frozen when moving character
- After minigame player returns to same spot rather than the start of the level

To do:
- Allowing enemies to be taken down by projectiles
- Adding music and sound effects to the game
- Adding an enemy to chase the player increasing difficulty
- Adding more levels to the game

## Acknowledgements
Give credit here.
- This project was inspired by games (Pokemon, The Legend of Zelda), Guides ([80's Rockstar Maze](https://arcade.makecode.com/--skillmap#rockstar))
- This project was based on [Tutorial 5 Computer History and Introduction to Microsoft Makdecode Arcade](https://canvas.uts.edu.au/courses/33108/files/8081046?module_item_id=2021301).

## Contact
Created by Nathan Ngo (13777406)
