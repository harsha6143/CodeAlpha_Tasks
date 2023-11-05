import random
word_list = ["mercedesbenz","ford","bmw","astonmartin","toyoto","lamborghini","bentley","rollsroyce","jeep","audi","ferrari"]
def choose_random_word():
    return random.choice(word_list)
def display_word(word, guessed_letters):
    display = ""
    for letter in word:
        if letter in guessed_letters:
            display += letter
        else:
            display += "_"
    return display
def play_hangman():
    word_to_guess = choose_random_word()
    guessed_letters = []
    attempts = 6
    print("Welcome to Hangman!")
    while True:
        print("\nWord: " + display_word(word_to_guess, guessed_letters))
        print("Attempts left: " + str(attempts))
        guess = input("Guess a letter: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single letter.")
            continue
        if guess in guessed_letters:
            print("You've already guessed that letter.")
            continue
        guessed_letters.append(guess)
        if guess not in word_to_guess:
            attempts -= 1
            print("Incorrect guess!")
        if "_" not in display_word(word_to_guess, guessed_letters):
            print("\nCongratulations! You've guessed the word: " + word_to_guess)
            break
        if attempts == 0:
            print("\nGame over! The word was: " + word_to_guess)
            break
if __name__ == "__main__":
    play_hangman()







