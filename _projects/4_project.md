---
layout: page
title: Friday board game
description: C++-based solo adventure adapted from Friedemann Friese’s famous board game of the same name
img: assets/img/friday0.jpg
importance: 3
category: fun
---

# Friday
A project based on the famous card game Friday


 Game Discription

1.1 Short Intro

Friday is a C++-based solo adventure adapted from Friedemann Friese’s famous board game of the same name. 
The player (Friday) is trying to guide Robinson through the game to win the game, who must beat three rounds of hazards on the island of increasing difficulty levels and, after surviving that, win against two rounds of pirates without finally dying to leave the island. 

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/friday0.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


1.2 Game Components

58 fighting cards*:            
	18 Robinson starting cards；
	10 aging cards；
	30 hazzard/knowledge cards；
10 pirate cards；
22 life points。
Robinson has a health bar of initial 20 life points, and a fighting bar of initial 0 fighting points.
There are also a Robinson stack (with 18 initial knowledge cards shuffled), an aging pile (with 10 initial aging cards shuffled), and a hazzard pile (with 30 initial hazzard/knowledge cards shuffled) **


1.3 Four Steps of the Game:

Step 1 : Green, survival;
Step 2 : Yellow, survival;
Step 3 : Red, survival;
Step 4 : Pirates;

1.4 Playing The Game:

The game starts from the Green step (step 1):
	1. Draw two topmost hazzard/knowledge cards from the hazzard pile***, and choose one of the two cards as the actual hazzard card. Discard the other card on the hazzard discard pile.	

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/friday2.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/friday.jpg" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>

	2. Fighting against the hazzard:
	The hazzard card shows its [hazard name], [rest number of free cards], [hazzard value of the first 3 steps (green, yellow, red)].
	The player can draw one fighting card after another from the Robinson stack, until [rest number of free cards] becomes 0. Robinson Starting card shows [knowledge name], [fighting points], [life value required to remove this card: 1], and [possible special action]. Without additional conditions, the possible special action of a card can only be used once in this round, and players can choose whether to use them and the order in which they are used. [fighting points] and [possible special action] will help to increase the total fighting points value. When the total fighting points value is less than [the hazzard value of the step], the player can choose to consume additional life points to draw additional knowledge cards from the knowledge pile (1 knowledge card/-1 life value, 1aging card/ -2 life value), or pay for the difference between the hazzard value of this stage and the total fighting points. 


	3. Result of Fighting a Hazzard :

		Result A (succeed in fighting):
		When the final total fighting point is not less than the [hazzard value of this stage], the player succeed in fighting this hazzard. This 		hazzard/knowledge Cards is converted into corresponding Knowledge Cards, which are placed in the knowledge discard pile top as a reward (the 			original hazzard card no longer exists). The player can also choose to consume life points to destroy specified knowledge cards before 			proceeding to the next hazzard fighting.
		
		Result B (fail a fighting):
		When the final total fighting point is less than the [hazzard value of this stage] at this stage, it is determined that the fighting of 		this hazzard is failed, and the hazzard/knowledge card will be placed in the hazzard discard pile as a crisis card. Players can choose to 		destroy any number of knowledge cards in this hand on the condition that their total [life values needed to remove this card] is lower than 		the paid life value. Then begin the next hazzard fighting.

Note: 
         The destroyed cards no longer enter any discard pile, but leave the whole round of the game.

	4. Step 1 ends when there are no remaining hazzard cards in the hazzard pile. Repeat the above process for step 2 (Yellow) and step 3 (Red). For [hazzard value of each step]: green < yellow < red. Hence Players should cleverly make each of their decision.

Notes: 
1) The removed cards no longer go into any discard pile, but leave the entire round of the game.
2) When there is only one hazzard card left in the hazzard pile, players can choose to challenge this hazzard card or go directly to the next step.
3) When the knowledge pile is exhausted, the system will put an aging card into the knowledge discard pile, then reshuffle the discard pile into the knowledge pile. The display on the aging card is similar to that of the knowledge card, the difference is: the fighting points are negative; [possible action] will be triggered mandatorily; the required life points to remove the card is 2.

	5. When the three stages are successfully cleared, enter step 4 (Pirates):

	6. The player draws two pirate cards from the pirate pile and chooses the order in which to challenge the two pirates.
	7. The display on the pirate card is similar to that of the crisis card, the differences are: [number of free cards] and [hazzard value] are 	larger; the life points consumed can only be used to draw additional knowledge cards, and cannot be used to offset the difference between the [hazzard value] and the total fighting points.

1.5 Game Victory
Players win the game after defeats two pirates with non-negative life points throughout the game.

1.6 Possible Action Types
Knowledge Cards: 
+  life(s), + card(s), destroy, double, copy, step-1, sort 3 cards, exchange
Aging Card: 
- life(s), highest card = 0, stop
(a detailed table will be put in Game Rules)

 Features List：

	1. Our game 「generates random game sets and events」, such as various fighting cards, unpredictable hazard cards, and knowledge cards, making the game exhilarating. We will use stand, rand, time.h combined with vector to realize shuffling.

	2. 「Dynamic memory management」 is realized by seven vectors to store all the hazard cards pile, fighting cards pile, aging cards pile, and corresponding discard pile as well as current cards.

	3. Information, including names, values, functions, etc., of each card is stored in a type 'Cards' created using struct. All cards are stored in an array of the class 'Cards'. 

	4. Regarding 「data structures for storing game status」, current gaming status will be stored in a type 'status' created using struct, which includes information like fighting values (int), the number of remaining free cards (int), hazard discard-piles (vector<int>), fighting piles (vector<int>), etc.

	5. As for 「loading/saving game status, file input/output」 are used. To be more specific, when storing, a file of type txt will be created as output with 'status' (containing current gaming status) written inside. When reentering the game, a file of type text will be read as input to 'status' (containing current gaming status).

	6. When it comes to 「program codes in multiple files」, there will be several files involved. They store basic functions such as refreshing the page, displaying standard interface, setting font color, shuffling, drawing cards (and displaying them), destroying cards, exiting the game with options of archiving or not. There will also be a file that stores all the cards' abilities and effects. All the text-based bulk information will also be stored in files separately, such as the background introduction and game rules files. The main program will also be written in a separate file, which contains a while infinite loop for the whole game, inside which is a while conditional loop in a single round accompanied with if-else, switch, cin, function call, etc.

	7. There are also colorful displaying interfaces and icons shown.


 A list of non-standard C/C++ libraries

	1.home_page.h
This library helps us to generate the home_page with looping, in which we are able to start the game or view the game rules.
	2.rules.h
This library helps us to read a large text file as input (fin) by iostream. With the help of looping inside, we will be directed to  the game after browersing the game rules.
	

 Compilation and execution instructions

	In order to quickly start the game we need to download 7 files to  a directory, namely, 
Makefile, main.cpp, rules.cpp, rules.txt, rules.h, home_page.cpp, home_page.h.
Then, we need to go to that  directory in terminal, and enter “make main”.
Next, we shall enter “./main” to run the programme. 

	

