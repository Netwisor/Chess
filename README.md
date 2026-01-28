# Chess Game with AI and Analysis

A fully-featured chess game with Stockfish AI integration and move analysis similar to Chess.com.

## Features

✅ **Complete Chess Implementation**
- All standard chess rules (castling, en passant, pawn promotion)
- Move validation and legal move highlighting
- Check, checkmate, and stalemate detection
- Move history with algebraic notation
- Captured pieces display

✅ **AI Opponent (Stockfish)**
- Play against Stockfish chess engine
- Adjustable difficulty levels (1-20)
- Smart move generation
- Real-time position evaluation

✅ **Game Analysis**
- Analyze your games like Chess.com
- Move classifications:
  - 💎 **Brilliant** - Outstanding tactical move
  - ⭐ **Great** - Very strong move
  - ✅ **Best** - Engine's top choice
  - 👍 **Good** - Solid move
  - ⚠️ **Inaccuracy** - Slight mistake
  - ❌ **Mistake** - Clear error
  - 💥 **Blunder** - Major mistake
- Accuracy percentage calculation
- Position evaluation display

✅ **Additional Features**
- Save/Load games in PGN format
- Move history navigation
- Resign and draw offers
- Local game storage
- Responsive design

## Setup Instructions

### Option 1: Using CDN (Recommended for Testing)

The current implementation tries to load Stockfish from CDN. However, due to CORS restrictions, this may not work in all browsers.

**To use the current version:**
1. Open `chess.html` in a modern web browser
2. If Stockfish doesn't load, see Option 2 below

### Option 2: Local Stockfish Setup (Recommended for Production)

For reliable Stockfish integration, download the engine locally:

1. **Download Stockfish.js:**
   - Visit: https://github.com/nmrugg/stockfish.js/releases
   - Download `stockfish.js` (or `stockfish.wasm.js` for better performance)
   - Place it in the same folder as `chess.html`

2. **Update the code:**
   - Open `chess.html` in a text editor
   - Find line ~1039: `stockfish = new Worker('https://cdn.jsdelivr.net/npm/stockfish.js@10.0.2/stockfish.js');`
   - Replace with: `stockfish = new Worker('stockfish.js');`
   - Do the same for line ~1070 (alternative CDN)

3. **Run with a local server:**
   ```bash
   # Using Python 3
   python -m http.server 8000
   
   # Using Python 2
   python -m SimpleHTTPServer 8000
   
   # Using Node.js (install http-server first: npm install -g http-server)
   http-server -p 8000
   ```
   
4. Open `http://localhost:8000/chess.html` in your browser

### Option 3: Using Lichess Stockfish API

Alternatively, you can use Lichess's free Stockfish API for analysis (requires internet connection).

## How to Use

### Playing Against AI

1. Click **"🤖 vs Stockfish"** button
2. Select AI difficulty level (1-20)
3. Make your move by clicking a piece and then clicking the destination square
4. Wait for the AI to respond
5. The engine status shows when AI is thinking

### Analyzing Games

1. Play a game or load a saved game
2. Click **"📊 Analyze"** button
3. Wait for the analysis to complete
4. View move classifications in the move history
5. Check the analysis panel for:
   - Current position evaluation
   - Move quality statistics
   - Overall accuracy percentage

### Move Classifications Explained

- **Brilliant (💎)**: A spectacular move that significantly improves your position, often involving a sacrifice
- **Great (⭐)**: An excellent move that gains a notable advantage
- **Best (✅)**: The engine's top recommended move
- **Good (👍)**: A solid move with minimal evaluation loss (<0.2 pawns)
- **Inaccuracy (⚠️)**: A suboptimal move losing 0.2-0.6 pawns
- **Mistake (❌)**: A clear error losing 0.6-2.0 pawns
- **Blunder (💥)**: A major mistake losing 2+ pawns or the game

### Saving and Loading Games

**Save:**
1. Click **"💾 Save"**
2. Copy PGN, download file, or save locally
3. Local saves are stored in browser storage

**Load:**
1. Click **"📂 Load"**
2. Paste PGN or select from saved games
3. Game will be replayed automatically

## Keyboard Shortcuts

- **Arrow Keys**: Navigate through move history
- **Home**: Go to start position
- **End**: Go to current position

## Browser Compatibility

- ✅ Chrome/Edge (Recommended)
- ✅ Firefox
- ✅ Safari
- ⚠️ Internet Explorer (Not supported)

## Troubleshooting

### Stockfish Not Loading

**Problem**: "Engine: Not available" message appears

**Solutions**:
1. Check browser console for errors (F12)
2. Try using a local server (see Option 2 above)
3. Download Stockfish locally instead of using CDN
4. Ensure JavaScript is enabled
5. Try a different browser

### Analysis Not Working

**Problem**: Analysis button doesn't work or gets stuck

**Solutions**:
1. Ensure Stockfish is loaded (check engine status)
2. Wait for current analysis to complete
3. Refresh the page and try again
4. Check that you have moves to analyze

### Slow Performance

**Solutions**:
1. Lower the AI difficulty level
2. Use stockfish.wasm.js for better performance
3. Close other browser tabs
4. Use a modern browser with WebAssembly support

## Technical Details

### Technologies Used
- Pure HTML5, CSS3, and JavaScript (no frameworks)
- Stockfish.js chess engine
- UCI (Universal Chess Interface) protocol
- PGN (Portable Game Notation) format
- LocalStorage for game persistence

### Move Evaluation Algorithm

The analysis uses Stockfish's evaluation to classify moves:
1. Analyze position before move
2. Analyze position after move
3. Compare evaluations
4. Classify based on evaluation difference
5. Adjust for player perspective (white/black)

### Performance Notes

- Analysis depth: 15 ply (configurable)
- AI search time: 500ms - 5000ms (based on level)
- Evaluation unit: centipawns (100 = 1 pawn)

## Future Enhancements

Potential features to add:
- Opening book integration
- Endgame tablebase support
- Time controls
- Online multiplayer
- Puzzle mode
- Tournament mode
- Export to various formats

## Credits

- Chess engine: [Stockfish](https://stockfishchess.org/)
- Stockfish.js: [nmrugg/stockfish.js](https://github.com/nmrugg/stockfish.js)
- Chess piece Unicode symbols

## License

This project is open source and available for personal and educational use.

---

**Enjoy your chess games! ♔♕♖♗♘♙**
