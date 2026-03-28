<div align="center">

# 🎴 UNO Console Game

**A feature-rich, text-based implementation of the classic UNO card game built entirely in Java.**

[![Java](https://img.shields.io/badge/Java-17+-ED8B00?style=for-the-badge&logo=openjdk&logoColor=white)](https://www.oracle.com/java/)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)
[![Platform](https://img.shields.io/badge/Platform-Console%20%2F%20CLI-grey?style=for-the-badge&logo=windowsterminal&logoColor=white)](/)
[![Status](https://img.shields.io/badge/Status-Complete-brightgreen?style=for-the-badge)](/)

*Play the beloved UNO card game right from your terminal — solo against a smart bot or with up to 4 friends!*

[Getting Started](#-getting-started) •
[Features](#-features) •
[Screenshots](#-screenshots) •
[Architecture](#-architecture) •
[Contributing](#-contributing)

</div>

---

## 📖 About

**UNO Console Game** is a fully-featured, terminal-based recreation of the iconic UNO card game. Built with clean **Object-Oriented Programming** principles in Java, the game delivers a smooth and colorful CLI experience complete with ANSI-colored cards, typewriter animations, and an intelligent bot opponent.

Whether you want a quick solo game against the bot or a multiplayer session with friends gathered around one terminal, this project brings the fun of UNO to the command line.

---

## ✨ Features

| Feature | Description |
|---|---|
| 🤖 **Smart Bot AI** | Play against an intelligent bot that strategically picks cards based on color frequency and card type |
| 👥 **Multiplayer** | Support for 2, 3, or 4 human players on the same terminal |
| 🎨 **Colored Output** | ANSI color-coded cards (🔴 Red, 🔵 Blue, 🟢 Green, 🟡 Yellow) for an immersive experience |
| 🔄 **Full UNO Ruleset** | Skip, Reverse, Draw Two, Wild, and Wild Draw Four — all action cards implemented |
| 🏆 **Leaderboard & Scoring** | Track scores across multiple rounds with a ranked leaderboard |
| ⚡ **UNO Call Mechanic** | Forget to type "UNO" when you're down to one card? That's a 2-card penalty! |
| 🎬 **Typewriter Animations** | Smooth text animations and timed reveals for a polished feel |
| 🔁 **Multi-Round Support** | Play multiple rounds in a single session with persistent scoring |

---

## 📸 Screenshots

<div align="center">

### 🏠 Game Menu & Mode Selection
<img src="screenshots/Capture d'écran 2026-03-28 150343.png" alt="Game Menu" width="500"/>

> *Choose between Player vs Bot, 2 Players, 3 Players, or 4 Players mode.*

---

### 🃏 Gameplay — Player Turn
<img src="screenshots/Capture d'écran 2026-03-28 150550.png" alt="Gameplay" width="700"/>

> *View your hand, playable cards, and choose your next move. Cards are color-coded for easy identification.*

---

### 🎮 Turn Start Screen
<img src="screenshots/Capture d'écran 2026-03-28 150422.png" alt="Turn Start" width="500"/>

> *Clean, focused UI for each player's turn with privacy protection in multiplayer.*

</div>

---

## 🚀 Getting Started

### Prerequisites

- **Java 17** or higher — [Download here](https://www.oracle.com/java/technologies/downloads/)
- A terminal that supports **ANSI color codes** (Windows Terminal, Git Bash, macOS Terminal, Linux Terminal)

### Installation

```bash
# 1. Clone the repository
git clone https://github.com/yourusername/UNO-Console-Game.git

# 2. Navigate to the project directory
cd UNO-Console-Game

# 3. Compile the source files
javac -d bin src/**/*.java

# 4. Run the game
java -cp bin game.Drive
```

### Quick Start with Eclipse

1. **Import** the project into Eclipse (`File → Import → Existing Projects`)
2. **Run** `Drive.java` as a Java Application
3. **Enjoy!** 🎉

---

## 🏗 Architecture

The project follows a **clean, modular architecture** using core OOP principles — inheritance, polymorphism, encapsulation, and abstraction.

### 📂 Project Structure

```
UNO-Console-Game/
├── src/
│   ├── cards/                    # Card hierarchy (Abstract → Concrete)
│   │   ├── Card.java             # Abstract base class
│   │   ├── ColoredCard.java      # Abstract colored card
│   │   ├── NumberedColoredCard.java
│   │   ├── DrawTwoCard.java
│   │   ├── ReverseCard.java
│   │   ├── SkipCard.java
│   │   ├── WildCard.java         # Abstract wild card
│   │   ├── WildColorCard.java
│   │   └── WildColorDrawFourCard.java
│   │
│   ├── deck/                     # Deck management
│   │   ├── Deck.java             # Abstract deck
│   │   ├── DrawPile.java         # Draw pile with shuffle & refill
│   │   └── DiscardPile.java      # Discard pile
│   │
│   ├── player/                   # Player management
│   │   ├── Player.java           # Player entity (human & bot)
│   │   └── PlayerHand.java       # Hand management
│   │
│   ├── enumTypes/                # Game enumerations
│   │   ├── Color.java            # RED, BLUE, GREEN, YELLOW
│   │   └── Number.java           # ZERO through NINE
│   │
│   └── game/                     # Game engine
│       ├── Drive.java            # Entry point (main)
│       ├── GameController.java   # Core game logic & rules
│       └── GameSession.java      # UI, I/O, and session management
│
├── screenshots/                  # Project screenshots
└── README.md
```

### 🧬 Class Diagram

<div align="center">
<img src="screenshots/Blank diagram.png" alt="UML Class Diagram" width="800"/>

> *UML Class Diagram showing the complete inheritance hierarchy and relationships.*
</div>

### 🎯 Design Highlights

- **Abstract Card Hierarchy** — `Card` → `ColoredCard` / `WildCard` → Concrete cards. Each card type implements its own `matches()` and `applyEffect()` logic via polymorphism.
- **Separation of Concerns** — `GameController` handles rules and state, `GameSession` manages UI and player interaction, and `Drive` serves as the entry point.
- **Bot Strategy Pattern** — The bot selects cards based on a scoring algorithm that evaluates color frequency and card type in its hand.
- **Standard 108-Card Deck** — Faithfully implements the official UNO deck composition.

---

## 🎮 How to Play

1. **Start the game** and choose a game mode (Player vs Bot or Multiplayer)
2. **Enter player names** when prompted
3. On your turn:
   - View the **top card** on the discard pile
   - See your **hand** and **playable cards**
   - **Select a card** to play, or **draw** if you have no valid moves
4. **Action cards** trigger immediately:
   - 🔄 **Reverse** — Changes the turn direction
   - 🚫 **Skip** — Skips the next player
   - ➕2 **Draw Two** — Next player draws 2 cards and loses their turn
   - 🌈 **Wild** — Choose any color to continue
   - 🌈➕4 **Wild Draw Four** — Choose a color + next player draws 4 cards
5. **Say UNO!** — Type `uno` when finishing your turn with 1 card remaining, or face a 2-card penalty
6. **Win** by being the first player to empty your hand!

---

## 🛠 Tech Stack

| Technology | Purpose |
|---|---|
| **Java 17+** | Core language with modern switch expressions |
| **OOP** | Inheritance, polymorphism, encapsulation, abstraction |
| **ANSI Escape Codes** | Terminal colors and text styling |
| **Collections Framework** | `ArrayList` for dynamic hand & deck management |
| **Scanner** | Terminal input handling |

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### 💡 Ideas for Contribution

- [ ] Add network multiplayer support
- [ ] Implement a tournament mode
- [ ] Add card stacking rules (stack Draw Two on Draw Two)
- [ ] Create a difficulty setting for the bot AI
- [ ] Add save/load game functionality

---

## 📄 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👤 Author

**Haroune** — *Developer & Designer*

- GitHub: [@haroune-dev](https://github.com/haroune-dev)

---

<div align="center">

**⭐ If you enjoyed this project, consider giving it a star! ⭐**

</div>
