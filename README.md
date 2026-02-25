# ♞ Single-File Chess Engine

A fully functional, lightweight Chess game with a built-in AI opponent, running entirely within a single HTML file. No servers, no installations, and no external libraries required.

![Status](https://img.shields.io/badge/Status-Playable-brightgreen)
![Tech](https://img.shields.io/badge/Tech-HTML%20%7C%20CSS%20%7C%20JS-blue)

Play at https://sk-chess.pages.dev/
---

## ✨ Features

*   **Zero Dependencies**: The entire game (Logic, UI, Styles) is contained in one file.
*   **Smart AI**:
    *   Uses the **Minimax Algorithm** with Alpha-Beta pruning.
    *   Includes **Piece-Square Tables** (PST) so the AI understands positional play (e.g., controlling the center).
    *   3 Difficulty Levels (Easy, Medium, Hard).
*   **Advanced Chess Rules Implemented**:
    *   ✅ **Castling** (Kingside & Queenside).
    *   ✅ **En Passant** capture.
    *   ✅ **Pawn Promotion** (Auto-queens upon reaching the last rank).
    *   ✅ **Check & Checkmate** detection.
*   **Modern UI**:
    *   **Visual Hints**: Shows available moves (dots) and capture targets (rings) when a piece is selected.
    *   **Highlights**: Shows the last move made, selected piece, and King in check.
    *   **Responsive**: Scales to fit mobile screens and desktops.

## 🚀 How to Play

### 1. Installation
There is no installation! Since this is a client-side web application:

1.  Download the `chess-pro.html` file (or copy the code into a text editor and save it as `chess.html`).
2.  Double-click the file to open it in any modern web browser (Chrome, Firefox, Safari, Edge).

### 2. Controls
*   **You play as White** (at the bottom). The Computer plays as Black.
*   **Click a piece** to select it. Valid moves will appear as faint dots on the board.
*   **Click a destination** to move the piece.
*   **Difficulty**: Use the dropdown menu at the bottom to change the AI strength.
    *   *Easy*: Makes random errors, good for beginners.
    *   *Medium*: Looks 2 moves ahead.
    *   *Hard*: Looks 3 moves ahead (may take a second to think).

## 🛠️ Technical Details

For developers interested in how it works:

### State Management
The board is represented as an 8x8 2D array. Strings represent pieces (e.g., `'P'` for White Pawn, `'q'` for Black Queen).
```javascript
// Example Board State
[
  ['r','n','b','q','k','b','n','r'], // Black pieces
  ['p','p','p','p','p','p','p','p'],
  ...
]
```

### Move Generation
The engine generates "pseudo-legal" moves based on piece geometry, then filters them by checking if the King is left in check (`movePutsKingInCheck`).

### The AI
The AI uses a recursive **Minimax** function:
1.  **Evaluation**: Calculates a score based on material difference (Queen=90, Pawn=10) + positional bonuses (Knights prefer the center).
2.  **Search**: It recursively simulates moves up to the selected depth.
3.  **Optimization**: It uses basic Alpha-Beta pruning to stop calculating branches that are already worse than a previously found move.

## 🎨 Customization

Since the code is in one file, you can easily tweak it:

*   **Change Colors**: Look for the `:root` section in the `<style>` tag to change board colors:
    ```css
    :root {
        --light-sq: #ebecd0; /* Change light squares */
        --dark-sq: #739552;  /* Change dark squares */
    }
    ```
*   **Adjust AI Aggression**: Modify the `PST` (Piece-Square Tables) or `PIECE_VALUES` in the JavaScript section to make the AI value capturing pieces more than positioning.
