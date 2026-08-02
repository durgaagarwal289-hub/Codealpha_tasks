#hangman game
import random

  # Hangman stages
stages = [
'''
 -----
 |   |
 |
 |
 |
 |
---------
''',
'''
 -----
 |   |
 |   O
 |
 |
 |
---------
''',
'''
 -----
 |   |
 |   O
 |   |
 |
 |
---------
''',
'''
 -----
 |   |
 |   O
 |  /|
 |
 |
---------
''',
'''
 -----
 |   |
 |   O
 |  /|\\
 |
 |
---------
''',
'''
 -----
 |   |
 |   O
 |  /|\\
 |  /
 |
---------
''',
'''
 -----
 |   |
 |   O
 |  /|\\
 |  / \\
 |
---------
'''
]

word_list = ("mango", "codealpha", "banana", "python","programming", "hangman", "computer", "science", "algorithm", "function")
word_list = random.choice(word_list)
guessed_letters = []
lives = 6

print("welcome to hangman game ")   

while lives > 0:
    display = " "
    for letter in word_list:
        if letter in guessed_letters:
            display += letter+""
        else:
            display += "_"
    print("\nword:", display)
    print(stages[6-lives])
    
    if "_" not in display:
        print("congratulations,you won the game!,you guessed the word:", word_list)
        break
    guess = input("guess a letter: ").lower()
    if guess in guessed_letters:
        print("you already guessed that letter")
        continue
    guessed_letters.append(guess)
    if guess not in word_list:
        lives -= 1
        print("wrong! lives left:", lives)
    print("lives left:",lives)

    if lives==0:
        print(stages[6])
        print("game over!")
        print("the word was:", word_list)
