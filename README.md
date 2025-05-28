import random
def choose_words():
    words = ["python", "hangman", "programming", "computer", "algorithm", "developer"]
    return random.choice(words)
def display_word(word, guessed_letters):
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter
        else:
            display += "_"
    return display
def hangman():
    word = choose_word()
    guessed_letters = []
    attempts = 6
    print("Welcome to Hangman!")
    while attempts > 0:
        print("\nWord:", display_word(word, guessed_letters))
        print("Attempts remaining:", attempts)
        guess = input("Guess a letter: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print("Invalid input. Please enter a single letter.")
            continue
        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue
        guessed_letters.append(guess)
        if guess in word:
           print("Correct guess!")
           if "_" not in display_word(word, guessed_letters):
                print("Congratulations! You guessed the word:", word)
                return
           else:
               print("Incorrect guess.")
               attempts -= 1
    print("\nGame Over. The word was:", word)
if __name__ == "__main__":
    hangman()
