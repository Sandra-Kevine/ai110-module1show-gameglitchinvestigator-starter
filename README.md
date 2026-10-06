# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [x] Describe the game's purpose: A simple number-guessing game built with Streamlit where the player tries to guess a secret number between 1 and 100, with hints after each guess.
- [x] Detail which bugs you found: (1) The "Too High"/"Too Low" hint text was swapped with the wrong direction, (2) the secret number was converted to a string on every other guess, breaking comparisons, (3) after winning, clicking "New Game" didn't reset the win status, so the game stayed stuck saying "You already won."
- [x] Explain what fixes you applied: Swapped the hint text so it matches the actual status, removed the string-conversion logic so `secret` always stays a number, and added a line resetting `status` to `"playing"` inside the New Game logic.

## 🎮 Demo Walkthrough

1. Run the app with `python3 -m streamlit run app.py` and open it in the browser.
2. Open "Developer Debug Info" to see the secret number.
3. Guess a number higher than the secret — the hint correctly says "Go LOWER!"
4. Guess a number lower than the secret — the hint correctly says "Go HIGHER!"
5. Guess the exact secret number — the game shows "Congratulations" and the win message.
6. Click "New Game" — the game resets fully and is immediately playable again, with no leftover "You already won" message.