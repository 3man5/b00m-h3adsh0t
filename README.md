
# b00m-h3adsh0t! &#x1F537;
**Neural Network Configurable Aimbot for First-Person-Shooter Games in C/C++** *Note: Aimbots are cheats and illegal in gaming leagues. This repo is solely for educational purposes only.*

> **┬┴┬┴┬┴┤ (҂   ` ﾛ ´)︻デ═一____________________＼(º □ º )/	├┬┴┬┴┬┴┬┴┬┴┬┴┬┴┬┴┬┴┬┴┬┴**

<div>
  
  [![Status](https://img.shields.io/badge/status-work--in--progress-success.svg)]()
  [![GitHub Issues](https://img.shields.io/github/issues/lucylow/b00m-h3adsh0t.svg)](https://github.com/lucylow/Mrs.Robot/issues)
  [![GitHub Pull Requests](https://img.shields.io/github/issues-pr/lucylow/b00m-h3adsh0t.svg)](https://github.com/lucylow/b00m-h3adsh0t/pulls)
  [![License](https://img.shields.io/bower/l/bootstrap)]()

</div>

## Table of Contents &#x1F537;

* [Motivation](https://github.com/lucylow/b00m-h3adsh0t#motivation)
* [Aimbot Neural Network](https://github.com/lucylow/b00m-h3adsh0t#aimbot-neural-network-)
* [Neural Network Model Training Recognition](https://github.com/lucylow/b00m-h3adsh0t#neural-network-model-training-recognition-)
* [How a normal aimbot works](https://github.com/lucylow/b00m-h3adsh0t#how-a-normal-aimbot-works-)
* [How b00m-h3adsh0t works](https://github.com/lucylow/b00m-h3adsh0t#how-b00m-h3adsh0t-works-)
* [Client-Server Backend Implementation](https://github.com/lucylow/b00m-h3adsh0t#client-server-backend-implementation-) 
* [Security and Efficiency Game Server](https://github.com/lucylow/b00m-h3adsh0t#security-and-efficiency-game-server-)
* [Player Behavior Statistics](https://github.com/lucylow/b00m-h3adsh0t#player-behavior-statistics-)
* [User Privacy](https://github.com/lucylow/b00m-h3adsh0t#user-privacy-)
* [Player Attacks](https://github.com/lucylow/b00m-h3adsh0t#player-attacks-) 
* [Glitches and Modifications](https://github.com/lucylow/b00m-h3adsh0t#glitches-and-modifications-) 
* [Conclusion](https://github.com/lucylow/b00m-h3adsh0t#conclusion-) 
* [References](https://github.com/lucylow/b00m-h3adsh0t#references-) 

## Motivation
* **B00m-h3adsh0t is a game bot software for first-person shooting (FPS) games** where players need to constantly move, think, strategize, and shoot enemies all at once. **Aimbot uses game data to automatically shoot at the heads of energy targets.**

* **Personal motivation to learn C++ compiler programming language, object oriented programing, and how a FPS game executes on an operating system**. B00m-H3adsh0t is 100% written in C++ with Visual Studio compiler providing a very fast, and efficient framework with scripting support such that the framework uses a consistent object-oriented design

  ![](https://github.com/lucylow/b00m-h3adsh0t/blob/master/readme-images/logo2.png)
  
  *Image. “Turn off Lucy's b00m-h3adsh0t aimbot you noob K/D ratio hacker!"*




## Aimbot Neural Network &#x1F537;

* **Trained by neural network (NN) with customizable predictions and dynamic speed settings**
* Select which FPS game you will use 
* **Engine-Aim with colored models:**
  * Hook into the FPS game engine to use actual game data to auto-aim without altering gaming files
  * Code won't work by itself because we need a handle to the game
  * Modifies memory of RAM half-life runs on 
  * Gathers information from current game and pixel location
  
    ![](https://github.com/lucylow/b00m-h3adsh0t/blob/master/readme-images/gameplay1.png)

    *Image. Custom training mode on the aimbot with a range of functionalities*

* **Custom training mode**
  * Leverage neural network to detect objects for object recognition using computer vision algorithms
  * Train with range of distances, lights, and angles for best possible recognition  

## Neural Network Model Training Recognition &#x1F537;
  
**Deep Reinforcement Learning**
  * Allows bot to learn how to aim by interacting with its unknown 3D environment
  * Bot receives a reward if it correctly kills an enemy, hence the name b00m-h3adsh0. If the bot dies, it gets a penalty.
  * For each step, bot observes the current states Ot of the environment and decides of an action
  * Observes reward signal where the goal of the agent is to find a policy that maximizes the expected sum of discounted rewards
  * Game states are partially observable

**Q-Learning Adaptation**
  * Used a Q-Learning adaptation for Deep Learning to train the autonomous agent
  * Inputs are screenshots of the fps game (pixels)
  * Deep reinforcement learning allows bot to learn game features simultaneously along with minimizing a Q-learning objective

**Dynamic Bayesian Network** 
  * Common for aimbot detections in FPS games
  * Used for probabilistic modeling and inference in discrete-time
  * Implementation options: 
    * libDAI - A free and open source C++ library for Discrete Approximate Inference in graphical models (C++)
    * Mocapy++ (C++) - A toolkit for inference and learning in dynamic Bayesian networks


## How a normal aimbot works &#x1F537;

* **Aimbot can be easily toggled on and off using the mouse or keyboard**
* Recognizes game objects in a certain range, then aims at the objects using game physics

* **Memory Searcher with Cheat Engine** 
  * Understand the memory storage structures within a game 
  * Searching memory to find the values of the player classes such as player coordinates, health, mouse x,y coordinates, etc.
  * Use **Cheat engine** to find addresses (programs that scans memory depending on the search details you give it and returns the memory addresses) 
  * Base address of "client.dll" (int or DWORD)
  * Read and write to the game memory 
    * Call the functions **ReadProcessMemory (RPM)** and **WriteProcessMemory (WPM)** 
    * Use multi-level pointers to access information to playerObjectAddress
* **CalcAngle**
  * Needed to calculate angle functions for aimbot since everything is based on game coordinates
  * Takes two 3D positions in source and distance, and outputs the angle to distance in angles
  * Pass in the local player's eye position into src, the target's head in dst, and then set the view angles from angles
* **Call Game Functions** 
  * For internal hacks where we need to inject DLL 
  * C++ programs call funtion by address via function pointers
  * **Traceline and RayTrace** commonly used in aimbots: 
    * Draws a line between your player and another player
    * Checks if there are objects in the way
    * If there are no collisions between you and your target  your aimbot should aim and shoot at that target
* **Game Player Detection** 
  * FPS game memory contains the **(X,Y,Z) coordinates of each player for rendering**
  * Aimbot scans memory locations for this information 
  * **Gain access to two key positions** - the player and enemies coordinates 
  * Subtracting the two positions as vectors == the vector between the two 
  * Calculate the **angle from the player's current vector to the desired angle vector**

* **Aim Automatically**
  * Inject information directly to the game
    * DLL injection
    * **Overwriting current FPS game aim functions**
    * Patching in-place the Direct3D or OpenGL DLL 
  * Examining the **functions calls to draw geometry**
  * Insert own geometry functions (for things like wall-hacks or glitches)
  * Fine-tune with constants adjusting for any **dynamic data structure moving players** around on you


## How b00m-h3adsh0t works &#x1F537;

* **Neural Network** 

    * Program takes **multiple screenshots** to recognize objects 
    * Different distances, lights, angles for best possible recognition 
    * Output - program writes in **cfg file** 
      * Batch = 1
      * Subdivision = 1 for testing 
    * Graph of **Training/Validation Set**
      * Graph x vs y 
      * Error Rate vs Number of Iterations in Training Set 
      
* **Training Depenencies - Trained Files for Games**

    * Use **b00m-h3adsh0t.cfg file** to change the resolution range for object recognition  
    * Train Files Folder
      * Darknet folder/subfolders 
      * Data or back up
      * GAME.names
      * GAME.cfg
      * GAME_last.weights 
      * GAME.weights
## Client-Server Backend Implementation &#x1F537;

* Computer has to display the gameplay to the user by rendering the whole map and every player in it

* **Client–Server Model Method**

  * Model instantaneously calculating/sending game results
  * **Client sessions run synchronously with aimbot server with user input data**
  * Run aimbot purely on game server
  * Run server mirrors client gameplay and continuously validates each game state
 
* **Modifying Game Rules World Method**

  * Aimbot targets servers with no rule enforcement or data integrity 
  * **Synchronize all client data with information about all of the other clients** 
    * Reveals where all the players in the game are via (X,Y,Z) coordinates
    * Reveals user game states with information on player names, position, clip ammo, ammo count, health, class, weapons, frame rate and more.
  * Data from client will allow player to break game rules, manipulate server, or manipulate other clients

## Security and Efficiency Game Server &#x1F537;

* Server responsible for information security and enforcing game rules

* **Sending Game World State needed for Immediate Display**
  * Results in client lag under bandwidth constraints

* **Sending the Player the Entire World State**
  * Results in faster display for  player under the same bandwidth constraints
  * Exposes  data to interception or manipulation
  * Trade-off between security and efficiency

## Player Behavior Statistics &#x1F537;
Refer to playerdata.h file 

* **Aimbot Evaluation Metrics**
  * Compare human player with b00m-h3eadsh0t agent 
  * K/D Ratio to compare ratio of kills to deaths 
  * Single player vs multi-player games 

* **Pattern Detection Systems**
  * Scan player's hard drives for known cheat code or programs
  * Scan player's system memory for known cheat code or programs
  * Labor-intensive to constantly track down cheats and update detection patterns

* **Anti–Cheat Method**
  * Guaranteed to work on all end–user system configurations
  * Reduce the amount of false positives

* **Player Behavior Anomalie Detection** 
  * Detected by statistically analyzing game events 
  * Data sent by client to  server by statistical detection systems
  * Add human element of supervision system (community/admin team looks over player statistics) 
  
      ![](https://github.com/lucylow/b00m-h3adsh0t/blob/master/readme-images/gameplay2.png)
      
      *Image. Unusual player behavior leads to clientside creating then uploading a gamer report*

## User Privacy &#x1F537;

* **End–users concerned with privacy issues and "Never trust the client" is common saying with game developers**
* VAC (Valve Anti-Cheat) accessing browsing history
* User privacy compromised with packet interception/manipulation 
* **Man-in-the-Middle Attack**
  * Reverse engineer the network packet formatting
  * Security of game circumvented by intercepting or manipulating data in real-time while transit from the client to the server or vice versa
  * Performed on client machine itself or via external communication proxy
  * Can provide player positions and other useful related information
  * Forged packets sent to server to move the player, shoot, or other game actions

## Player Attacks &#x1F537;

* **Select button to attack and enable/disable training mode**
* Custom zooming control with scroll wheel 
* Custom crosshairs
* Laser sight
* Trigger bot
* Move speed
* Ammo count
* Player radar 
* Name-tag display to detect players 
* Auto shoot/rapid fire
  * Most fps games limit the rate weapons are fired regardless of how fast a player presses buttons
  * Binding the firing button to the scroll wheel of a mouse
  * Macro setting that will simulate rapid key presses automatically
  * Set aiming speed and shooting delay
* Auto clicker for semi automatic weapons 
* Dynamic recoil control  
  * Remove gun revoil game element
  * Control bullet spread
  * Correcting for bullet drop

## Glitches and Modifications &#x1F537;

* Wall hacks
  * Glitches with game surfaces
  * Graphics driver modifications that ignore depth checking
  * Draw all objects on the screen
* Reduced flash 
* Correcting for ping/lag
* Resolution range 
* Pixel memory hack
* Transparent buildings, ceilings, obstacles, and trees
  * Remove visual elements of the game 
  * Ex Replace opengl32.dll with one that would render polygons transparent 

* Display enemy lines 
* Extrasensory perception (ESP)
  * Display all the enemy positions on the map
  * Glowing or lighted players, weapons, and loot. 
  * See all players at all times and plan ahead before making a kill
  * Show all information ex: player names, position, clip ammo, ammo count, health, class, weapons, frame rate and more
## Conclusion &#x1F537;

B00m-h3adsh0t! is a single architecture neural network configurable aimbot for first-person shooting (FPS) games. We introduced a method to augment a deep reinforcement q-learning model with high-level game information, and feature implementation. We showed that b00m-h3adsh0t!  model is able to outperform built-in bots as well as human players and demonstrated the generalizability of our model to do game glitches and modifications. 


-------

## References &#x1F537;

* Machine Learning Paper. Aimbot Detection in Online FPS Games Using a Heuristic Method Based on Distribution Comparison Matrix: https://link.springer.com/chapter/10.1007/978-3-642-34500-5_77
* Exploting supervised learning techniques on game server collecting game data with decision trees, Naive Bayes, random forest, neural networks, and support vector machines. https://ieeexplore.ieee.org/abstract/document/6032016
* Multiple classificatoin system for neural networks http://ceur-ws.org/Vol-1659/paper7.pdf
* Bayesian Imitation Learning the ROute to Belivable Gamebots.  https://www.researchgate.net/profile/Christian_Bauckhage/publication/258510478_Is_Bayesian_imitation_learning_the_route_to_believable_gamebots/links/0c960539de8012b04e000000/Is-Bayesian-imitation-learning-the-route-to-believable-gamebots.pdf
* Towards a Fair n Square Aimbot. Machine Learning techniques for spatio-temporal improvements to aimbots. http://vampire-project.de/files/papers/Bauckhage2004-TAF.pdf
* Server side machine learning classifiers for anti-cheating in games using game logs https://ieeexplore.ieee.org/abstract/document/6633617
* Bayesian network paper on aimbot behavior detection. http://www.cs.cuhk.edu.hk/~cslui/PUBLICATION/detect_cheat.pdf
* Classifier systems for controlling NPCs in games. https://pdfs.semanticscholar.org/68cf/3f5b16c452b004d986dcbdefa6fc28fa1c9b.pdf 
* Game bot detection. Detecting user injections https://dl.acm.org/citation.cfm?id=1653694
* C++ code for applications of Dynamic Bayesian Network https://github.com/wengjn/MatlabDBN
* DBN++ Data Structures and Algorithms in C++ for Dynamic Bayesian Networks https://github.com/thiagopbueno/dbn-pp
* Paper Dynamic Bayesian Neytworks https://www.cs.ubc.ca/~murphyk/Papers/dbnchapter.pdf
* Paper A Bayesian Model for Plan Recognition in RTS (Real Time Strategy) Games https://www.aaai.org/ocs/index.php/AIIDE/AIIDE11/paper/viewFile/4062/4416
* Learning to Shoot in First Person Shooter Games by Stabilizing Actions and Clustering Rewards for Reinforcement Learning. https://arxiv.org/pdf/1806.05117.pdf
* CS:GO external hack base https://github.com/NullTerminatorr/NullBase
* FastML. Solve the cheaters problem in Counter Strike, with or without machine learning
http://fastml.com/how-to-solve-the-cheaters-problem-in-counter-strike-with-or-without-machine-learning/
