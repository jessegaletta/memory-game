# WebDev-FinalProject 🎮

> [!NOTE]
> **Academic Project**: Developed as the final project for the **Web Development** course at **EPICODE Institute of Technology**.
> 
> This repository contains the source code and documentation required for the examination.
> 
> 📄 **Official Requirements**: [Download Project Specifications (PDF)](docs/requirements.pdf)

---

## Project Topic 🧐

The classic **Memory** game has been implemented, where the goal is to guess pairs of images. 🖼️🧠

## Requirements ⚙️

- **Internet connection** 🌐
- **JSONBin** (see "Procedure for creating an empty database") 🗃️

The game's images are dynamically loaded using the link `https://picsum.photos/200?random=X`.  
*(X = random image number, each pair has the same number).* 🎲

## Procedure for Creating an Empty Database 📝

1. Create an account on [**JSONBin**](https://jsonbin.io/) and log in to the portal. 🔑
2. In the "API-KEY" section, create an "X-Access-Key" with read and write permissions, as only GET and PUT requests are made. 🔒
3. In the "BINS" section, create a new file with the following structure:

    ```json
    {
      "users": [],
      "scores": []
    }
    ```

4. Modify the two global variables (file bin URL and ACCESSKEY) in the `assets/js/server.js` file of the project. 🔧

## Implemented Features ✨

### Home Page (index.html) 🏠

Introductory page with a small memory game. When hovering the mouse, images are displayed. The only clickable element is the "Play Now" button.  
In this case, the positions of the images are static (this page was used to implement the game logic later). 🎮

### Login (login.html) 🔑

User and password verification (see "User session management" section). To log in, create a new user. 👤

### User Registration (register.html) 📝

A new user can be registered. It checks if the user has already been created, if the password and confirmation match, and if the birthdate is at least 5 years ago.  
No special password restrictions have been implemented, so there's no minimum character requirement or security rule. 🔒

### Password Recovery (forgot.html) 🔑❓

Procedure composed of 3 steps:

1. Enter username, email, and birthdate 📧🎂
2. Answer the security question 🔑
3. Enter a new password 🔐

### Game (game.html) 🎮

The core of the application. Once started, a timer of 1 minute begins as soon as a card is flipped. ⏱️ At the end of the game, the session is saved, and the player's ranking for the game score is shown (compared to the best score obtained). 🏆

#### Score Calculation ⚖️

- **Correct pair**: +100 points 🏅
- **Combo** (two consecutive correct pairs): +100 + 50 = +150 points 💥
- **Same card flipped twice**: -10 points ⚠️
- **Time bonus**: 5 points * remaining seconds ⏳

### Scores (scores.html) 🏆

The leaderboard of all games played by all users is displayed, and the best score achieved by the player is highlighted. 🌟

### Profile (profile.html) 👤

The user’s profile can be viewed, and personal and security details can be updated. 🔧

## User Session Management 🔑

Working only with JavaScript, I simulated the user session by storing the connected user's username in `localStorage` (see `assets/js/session.js`). 💾

## External APIs 🌍

- [**JSONBin**](https://jsonbin.io/)

This portal allows the management of JSON files via fetch requests. 🔄

In the absence of a backend, all the user and game score data is managed with a JSON file hosted on this portal. 🗄️

The server logic is simulated in JavaScript by manipulating this file (see `assets/js/server.js`). 🖥️
