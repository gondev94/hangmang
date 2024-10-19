import random

word_list = ["papa", "programación", "developer", "tenis", "python"]
chosen_word = random.choice(word_list)
lives = 6
stages = ['''
  +---+
  |   |
  O   |
 /|\  |
 / \  |
      |    
=========
''', '''
  +---+
  |   |
  O   |
 /|\  |
 /    |
      |    
=========
''', '''
  +---+
  |   |
  O   |
 /|\  |
      |
      |
=========
''', '''
  +---+
  |   |
  O   |
 /|   |
      |
      |    
=========
''','''
  +---+
  |   |
  O   |
  |   |
      |
      |    
=========
''','''
  +---+
  |   |
  O   |
      |
      |
      |
=========
''',''' 
  +---+
  |   |
      |
      |
      |
      |
=========
''',]

placeholder = ""
word_length = len(chosen_word)
for position in range(word_length):
    placeholder += "_"
    
print(placeholder)    

game_over = False
correct_letters = []
while not game_over:
    guess = input("Guess a letter: " ).lower()
    
    display = ""
    if guess in correct_letters:
        print(f"you have already entered this letter '{guess}'")
    
    for letter in chosen_word:
        if letter == guess:
            display += letter
            correct_letters.append(guess)
        elif letter in correct_letters:
            display += letter
        else:
            display += "_"
        
    print(display)
    if guess not in chosen_word:
        lives -= 1
        print(f"You guessed '{guess}' that's not in the word, yo lose a life '{lives}' lifes left")
        if lives == 0:
            game_over = True
            print(f"!You lose! this is the secret word {chosen_word}")
    if "_" not in display:
        game_over = True
        print("!You win!")
    print(stages[lives])
     
        
