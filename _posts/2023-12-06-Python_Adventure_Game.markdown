---
layout: post
title: Karma Got You! (Choose Adventure Game)
date: 2023-12-06
description: You’ll find this post in your `_posts` directory. Go ahead and edit it and re-build the site to see your changes. # Add post description (optional)
img: python_choose_adventure.png # Add image post (optional)
tags: [Python,Choose_Adventure_Game,CISC179,Final_Project,Intro_Python] # add tag
---
## Summary of Game
"Karma Got You!" is a choose your own adventure game with a built in mini game of an alternative to rock paper scissors. For Introduction to Python (CISC 179), we were tasked with an open ended final project. The assignment was to create a program that has a specific function and that uses at least 4 core concepts that we learned. In my program I used user input and interaction, if/else statements, functions, while loops, and python's random and time modules. 

In "Karma Got You!" you follow your dog that has been kidnapped by a strange gnome who wants to play "Rock, fire, ice" with you. Below you will find the code I wrote for this game. Please have fun trying it out.

<pre><code class="language-python">
import random
import time

# Create list of options for "rock, fire, ice" game, an alternative to "rock, paper, scissors."

options = ["rock", "fire", "ice"]
you_won = "\"You won fair and square. I release you from my lair. By the following decree, reunited you will be.\"\n૮ ˆﻌˆ ა"


# Build function that includes dialogue surrounding the game of "rock, fire, ice" as well as code to conduct the game itself. The game consists of a single round where the user either immediately wins or looses. In case of a tie another round is played. If the user wins the game of rock, fire, ice, they win the whole game and the game ends. If the player looses the game of rock, fire, ice, the whole game also ends. The user is prompted to type "rock," "fire," or "ice" and the answer is compared to the gnomes choice which is generated randomly. Rock beats fire, fire beats ice, and ice beats rock. If the user enters an invalid response the program will continue to ask them to write a response.

def rock_fire_ice():
    print(f"\"Delightful {name}! If you win, I will give you your dog back and return both of you home."
          f"\nIf you loose, you will both stay here forever."
          f"\nReady set shoot!\"")
    random.seed(time.time())
    while True:
        user_throw = input("\nThrow rock, fire, or ice: ").lower()
        random_number = random.randint(0, 2)
        gnome_throw = options[random_number]
        if user_throw in options:
            print(f"The gnome threw {gnome_throw}")
        else:
            continue
        if user_throw == "rock" and gnome_throw == "fire":
            print(you_won)
            quit()
        elif user_throw == "fire" and gnome_throw == "ice":
            print(you_won)
            quit()
        elif user_throw == "ice" and gnome_throw == "rock":
            print(you_won)
            quit()
        elif user_throw == gnome_throw:
            continue
        else:
            print("You lost. You and your dog will stay forever in the gnome's meadow.")
            quit()


# Build function for scenario where user progresses into the game beyond the introductury portion. The "snatch_foot" scenario occurs on two different paths in the game, so a function was used. In this part of the game the user is snatched into a portal where they meet the gnome. They are given options to interact with the gnome. If the correct option is chosen, the gnome invites the user to play "rock, fire, ice." If a non-existent option is chosen, the game ends.

def snatch_foot():
    print("\nA hand comes out of the darkness, snatches your foot, and pulls you through a portal."
          "\nYou appear on a sunny meadow of flowers. The gnome stands before you with a devilish grin."
          f"\n\"I've been waiting for you {name}\" says the gnome.")
    answer_gnome = input("You a) scream, b) run away, c) wait for the gnome to speak again: ")
    if answer_gnome == "a":
        print("The gnome has a huge distaste for screams and sent you back to the beginning.")
    elif answer_gnome == "b":
        print("You will never out run the gnome. RIP.")
        quit()
    elif answer_gnome == "c":
        while answer_gnome == "c":
            print(
                "The gnome speaks.\n\"Let's play rock, fire, ice. Rock beats fire, fire beats ice, and ice beats rock.")
            answer_play = input("Shall we play?\" ")
            if answer_play == "yes":
                rock_fire_ice()
                break
            else:
                print("The gnome only takes yes for an answer.")
    else:
        print("Great job! You hacked the game with an unavailable option."
              "..."
              "Just kidding, the gnome is not amused. You evaporate into thin air.")
        quit()


# This is the beginning or introductory portion of the game. Context is given and the user is given the option to join or not join the adventure. The user is asked to give their name.

print(
    "You are sitting at home coding when a gnome breaks into your room through the air vent and disappears with your dog."
    "\nWould you like to chase the gnome and save your dog?")
play_game = input("Type yes or no: ").lower()

if play_game == "yes":
    print("You have chosen to embark on an adventure.")
    name = input("What name will you use on this quest? ")
else:
    print("Karma will get you. Have a good day.")
    quit()

# The user is faced with three options of how to fall from the vent they jumped into. Option a brings the user back to choosing how to fall correctly. Option b takes the user on the main path to continue the game. This option uses the snatch_foot and rock_fire_ice functions. Option c is an alternate path that either ends in a dead end or continues on the same path as option b. If a non-existent option is chosen, the game ends.

while play_game == "yes":
    print(
        "You jump after the gnome into darkness. You slip on something and feel that you are falling."
        "\nDo you a) embrace for impact and curl into a ball, b) try to land on your toes, or c) grab on to the ledge sticking out of the wall?")
    answer_fall = input("Type a, b, or c: ").lower()
    if answer_fall == "a":
        print("You chose the wrong way to fall from heights. Try again.")
    elif answer_fall == "b":
        print(
            "You knew how to soften your fall. Luckily the fall wasn't too high and a pile of leaves was waiting for you.")
        snatch_foot()
    elif answer_fall == "c":
        print(
            "You grab on to the ledge and pull yourself up. The days you spent bouldering paid off and you're able to climb out of the vent."
            "\nHowever, you saved only yourself and your dog remains hostage.")
        answer_go_down = input("Would you like you like to go back down? ").lower()
        if answer_go_down == "yes":
            snatch_foot()
        else:
            print("The gnomes grew bold and you were next. Karma got you.")
            quit()
    else:
        print("You don't know the rules, you loose.")
        quit()
</code></pre>
