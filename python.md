import random


def start_game():    
    scores = [12]
    high_score = min(scores)

    print("""
    ==================================
    Welcome to the random number game!
    ==================================
    """)
    answer = random.randrange(1, 10)
    print("{} is the highscore".format(high_score))
    try:
        guess = int(input("Pick a number between 1-10:  "))

    except ValueError:
        guess = int(input("Please type a number:  "))
    score = 0


    while guess != answer:
        score += 1
        if guess > 10:
            guess = int(input("Oops, {} is higher than 10, try again:  ".format(guess)))
        elif guess < 1:
            guess = int(input("Oops, {} number is lower than 1, try again:  ".format(guess)))
        if guess > answer:
            guess = int(input("It's lower, try again:  "))
        elif guess < answer:
            guess = int(input("It's higher, try again:  "))


    if guess == answer:
        score += 1
        print("{} is correct! You have completed the game!".format(guess))
        scores.append(score)

        high_score = min(scores)
        print("You took {} tries".format(score))
        print("{} is the high score!".format(high_score))
        play_again = input("Would you like to play again? (Yes/No)  ")
        play_again = play_again.lower()
        if play_again == "yes":
            start_game()
        elif play_again == "no":
            print("Okay, have a nice day!")
        else:
            print("I'll take that as a no. Bye")


start_game()
