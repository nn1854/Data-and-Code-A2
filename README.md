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
How does one go about using it?
Provide various use cases and code examples here.

`write-your-code-here`

@namespace
class SpriteKind:
    NPC = SpriteKind.create()
    Warrior = SpriteKind.create()
# Player overlap (yellow chest)t

def on_overlap_tile(sprite52, location52):
    info.change_score_by(1)
    game.show_long_text("You have found a \"Shiny Sword\"", DialogLayout.BOTTOM)
    tiles.set_tile_at(location52, assets.tile("""
        Open Yellow
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Yellow Chest
    """),
    on_overlap_tile)

# Player movement (up)

def on_up_pressed():
    animation.run_image_animation(mySprite, assets.animation("""
        Move Up
    """), 200, True)
controller.up.on_event(ControllerButtonEvent.PRESSED, on_up_pressed)

# Creates a new level once achievements have been made
def createLevel():
    # Level 1 maze
    # Level 2 showing dragon
    # End game
    if level == 1:
        tiles.set_current_tilemap(tilemap("""
            Level 1
        """))
    elif level == 2:
        game.show_long_text("Goodluck hero, we are all counting on you",
            DialogLayout.BOTTOM)
        level2()
    controller.move_sprite(mySprite)
    tiles.place_on_random_tile(mySprite, sprites.castle.tile_path5)
    scene.camera_follow_sprite(mySprite)
# Player overlap (blue chest)

def on_overlap_tile2(sprite23, location23):
    info.change_score_by(1)
    game.show_long_text("You have found a \"Potion of Endurance\"",
        DialogLayout.BOTTOM)
    tiles.set_tile_at(location23, assets.tile("""
        Open Blue
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Blue Chest
    """),
    on_overlap_tile2)

# Player overlap (white chest)

def on_overlap_tile3(sprite4, location4):
    info.change_score_by(1)
    game.show_long_text("You have found a \"Fallen Feather\"", DialogLayout.BOTTOM)
    tiles.set_tile_at(location4, assets.tile("""
        Open White
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        White Chest
    """),
    on_overlap_tile3)

# Player overlap (purple chest)

def on_overlap_tile4(sprite22, location22):
    info.change_score_by(1)
    game.show_long_text("You have found a \"Royal Shield\"", DialogLayout.BOTTOM)
    tiles.set_tile_at(location22, assets.tile("""
        Open Purple
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Purple Chest
    """),
    on_overlap_tile4)

# Player projectiles

def on_a_pressed():
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

# Player release buttom

def on_button_released():
    animation.stop_animation(animation.AnimationTypes.ALL, mySprite)
controller.any_button.on_event(ControllerButtonEvent.RELEASED, on_button_released)

# Player movement (left)

def on_left_pressed():
    animation.run_image_animation(mySprite, assets.animation("""
        Move Left
    """), 200, True)
controller.left.on_event(ControllerButtonEvent.PRESSED, on_left_pressed)

# Countdown till game over

def on_countdown_end():
    game.game_over(False)
info.on_countdown_end(on_countdown_end)

# Level 2 with monsters
def level2():
    tiles.set_current_tilemap(tilemap("""
        Level 2
    """))
    scene.set_background_color(13)
    info.start_countdown(15)
# Player overlap (red chest)

def on_overlap_tile5(sprite6, location6):
    info.change_score_by(1)
    game.show_long_text("You have found a \"Ruby Ring\"", DialogLayout.BOTTOM)
    tiles.set_tile_at(location6, assets.tile("""
        Open Red
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Red Chest
    """),
    on_overlap_tile5)

# Player movement (right)

def on_right_pressed():
    animation.run_image_animation(mySprite,
        assets.animation("""
            Move Right
        """),
        200,
        True)
controller.right.on_event(ControllerButtonEvent.PRESSED, on_right_pressed)

# Player overlapping knight

def on_overlap_tile6(sprite, location):
    game.show_long_text("There are monsters blocking the path ahead",
        DialogLayout.BOTTOM)
    tiles.set_tile_at(location, assets.tile("""
        Knight 2
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Knight
    """),
    on_overlap_tile6)

# Player overlap (green chest)

def on_overlap_tile7(sprite32, location32):
    info.change_score_by(1)
    game.show_long_text("You have found a \"Lovely Potion\"", DialogLayout.BOTTOM)
    tiles.set_tile_at(location32, assets.tile("""
        Open Green
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Green Chest
    """),
    on_overlap_tile7)

# Player movement (down)

def on_down_pressed():
    animation.run_image_animation(mySprite, assets.animation("""
        Move Down
    """), 200, True)
controller.down.on_event(ControllerButtonEvent.PRESSED, on_down_pressed)

# Player overlapping king

def on_overlap_tile8(sprite5, location5):
    game.show_long_text("I can't get back because the monsters are blocking the way ",
        DialogLayout.BOTTOM)
    tiles.set_tile_at(location5, assets.tile("""
        King 2
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        King
    """),
    on_overlap_tile8)

# Finish level one, Player overlapping portal tile

def on_overlap_tile9(sprite24, location24):
    clearLevel()
scene.on_overlap_tile(SpriteKind.player,
    sprites.dungeon.collectible_insignia,
    on_overlap_tile9)

# Clears level and creates a new one
def clearLevel():
    global level
    for value in sprites.all_of_kind(SpriteKind.enemy):
        sprites.destroy(value)
    for value2 in sprites.all_of_kind(SpriteKind.Warrior):
        sprites.destroy(value2)
    level += 1
    createLevel()
# Player overlapping monster

def on_overlap_tile10(sprite3, location3):
    game.show_long_text("You're weapons scare us", DialogLayout.BOTTOM)
    game.show_long_text("We will allow you to pass", DialogLayout.BOTTOM)
    tiles.set_tile_at(location3, assets.tile("""
        Monster 2
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Monster
    """),
    on_overlap_tile10)

# Player overlapping female warrior

def on_overlap_tile11(sprite2, location2):
    game.show_long_text("Please help us hero!", DialogLayout.BOTTOM)
    tiles.set_tile_at(location2, assets.tile("""
        Female Warrior 2
    """))
scene.on_overlap_tile(SpriteKind.player,
    assets.tile("""
        Female Warrior
    """),
    on_overlap_tile11)

# Player score 6

def on_on_score():
    game.show_long_text("Congratulations you have found all the artefacts!",
        DialogLayout.BOTTOM)
    game.show_long_text("Find the portal and make your way back to the wizard",
        DialogLayout.BOTTOM)
info.on_score(6, on_on_score)

# Setting the layout and sprite for the game
def startLevel():
    global mySprite
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
    createLevel()
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
startLevel()

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
