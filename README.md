import random

def number_guessing_game():
    print("Welcome to the Number Guessing Game!")
    print("I'm thinking of a number between 1 and 100.")
    
    # Generate a random number between 1 and 100
    number_to_guess = random.randint(1, 100)
    
    # Initialize the number of attempts
    attempts = 0
    
    while True:
        # Ask the player for a guess
        user_guess = input("Enter your guess: ")
        
        # Validate the input to ensure it's a number
        try:
            user_guess = int(user_guess)
        except ValueError:
            print("Please enter a valid number.")
            continue
        
        attempts += 1
        
        # Check if the guess is correct
        if user_guess < number_to_guess:
            print("Too low! Try again.")
        elif user_guess > number_to_guess:
            print("Too high! Try again.")
        else:
            print(f"Congratulations! You guessed the right number {number_to_guess} in {attempts} attempts.")
            break

# Call the function to start the game
number_guessing_game()
