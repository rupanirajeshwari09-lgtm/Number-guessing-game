# Task 2: Number Guessing Game
# Using random, numpy, pandas, and matplotlib

import random
import numpy as np
import pandas as pd
import matplotlib.pyplot as plt

# Generate random number between 1 and 100
secret_number = random.randint(1, 100)

attempts = 0
guess_history = []

print("🎮 Welcome to the Number Guessing Game!")
print("Guess a number between 1 and 100")

while True:
    try:
        # User input
        guess = int(input("Enter your guess: "))
        attempts += 1

        # Store guesses
        guess_history.append(guess)

        # Check guess
        if guess < secret_number:
            print("📉 Too low! Try again.")

        elif guess > secret_number:
            print("📈 Too high! Try again.")

        else:
            print(f"🎉 Correct! The number was {secret_number}")
            print(f"✅ You guessed it in {attempts} attempts.")
            break

    except ValueError:
        print("❌ Please enter a valid number.")

# Convert guess history into pandas DataFrame
df = pd.DataFrame({
    "Attempt": np.arange(1, attempts + 1),
    "Guessed_Number": guess_history
})

print("\n📋 Guess History:")
print(df)

# Plot guesses using matplotlib
plt.plot(df["Attempt"], df["Guessed_Number"], marker='o')
plt.axhline(y=secret_number, linestyle='--')
plt.xlabel("Attempt Number")
plt.ylabel("Guessed Number")
plt.title("Number Guessing Game Analysis")
plt.grid(True)

plt.show()# Number-guessing-game