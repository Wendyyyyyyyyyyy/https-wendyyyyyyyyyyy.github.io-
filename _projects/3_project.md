---
layout: page
title: Big Two card game
description: implementing networking and multi-threading capabilities in Java, enabling four players to play over the internet
img: assets/img/2396.png
#redirect: https://unsplash.com
importance: 3
category: work
---


## Overview
This project focuses on enhancing the Big Two card game by implementing networking and multi-threading capabilities in Java, enabling four players to play over the internet. The provided classes and interfaces, including `BigTwoServer`, `CardGameServer`, `CardGameMessage`, `GameMessage`, and `NetworkGame`, will facilitate your implementation. You will develop a `BigTwoClient` class to model the client side of the game, manage game logic, and handle communication with the game server.

## Game Description
Big Two is a popular card game where the goal is to be the first to play all your cards. Each player is dealt 13 cards, and the game is typically played with a standard deck of 52 cards. The player with the 3 of Diamonds starts the game, and players take turns playing hands of increasing value. The hands can be singles, pairs, triples, or various poker hands.

<div class="row">
    <div class="col-sm mt-3 mt-md-0">
        {% include figure.liquid loading="eager" path="assets/img/2396.png" title="example image" class="img-fluid rounded z-depth-1" %}
    </div>
</div>


## Getting Started
To get started with the game:
1. **Launch the Game**: Run the `BigTwoClient` class. You will be prompted to enter your name.
2. **Connect to Server**: The client will establish a connection to the game server.
3. **Gameplay**: Once all players are connected and ready, the game will start. Play your cards by selecting them and pressing "Play" or pass your turn by pressing "Pass".
4. **Chat**: Use the text input field to send messages to other players during the game.

## Implementation Details
### Server Behavior
- **Connection Handling**: The server manages connections, sends player lists, handles disconnections, and broadcasts messages such as JOIN, READY, START, MOVE, and MSG to clients.
- **Game Start**: When all players are ready, the server broadcasts a START message with a shuffled deck.
- **Move Handling**: The server broadcasts MOVE messages to clients when a player makes a move.
- **Chat Messages**: The server relays chat messages between clients.

### Client Behavior
- **Name Entry**: Players enter their names at the start.
- **Server Connection**: The client connects to the game server using the provided IP and port.
- **Game Logic**: The client handles game logic, such as dealing cards, making moves, and checking moves.
- **Chat Functionality**: The client supports chat messages, which are displayed in the chat area.
- **Game End**: The client shows game results in a dialog box when the game ends.

### Class Specifications
#### `BigTwoClient`
- **Constructor**: Initializes players, GUI, and server connection.
- **Instance Variables**: Includes player list, hands on the table, player ID, server details, socket, output stream, current index, and game table.
- **Methods**: Implements methods for game logic, handling server messages, making moves, and managing the connection.

### Graphical User Interface (GUI)
- **Chat Area**: Displays chat messages.
- **Text Input Field**: Allows players to send chat messages.
- **Connect Menu Item**: Establishes a connection to the game server.

## Conclusion
Enhancing the Big Two card game with networking and multi-threading allows for a more interactive and engaging multiplayer experience. By following the specifications and implementing the necessary classes and methods, you can successfully create a networked version of the Big Two game. Enjoy coding and have fun playing Big Two online with your friends!
