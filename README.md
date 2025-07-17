# codeAlpha_HangmanGame
import random

def hangman():
    words = ['python', 'code', 'alpha', 'intern', 'script']
    word = random.choice(words)
    guessed = ['_'] * len(word)
    tries = 6
    guessed_letters = []

    print("Welcome to Hangman!")

    while tries > 0 and '_' in guessed:
        print("\nWord:", ' '.join(guessed))
        guess = input("Guess a letter: ").lower()

        if not guess.isalpha() or len(guess) != 1:
            print("Enter a single letter.")
            continue
        if guess in guessed_letters:
            print("You already guessed that.")
            continue

        guessed_letters.append(guess)

        if guess in word:
            for i in range(len(word)):
                if word[i] == guess:
                    guessed[i] = guess
            print("Good guess!")
        else:
            tries -= 1
            print("Wrong guess! Tries left:", tries)

    if '_' not in guessed:
        print("You won! The word was:", word)
    else:
        print("You lost. The word was:", word)

hangman()
