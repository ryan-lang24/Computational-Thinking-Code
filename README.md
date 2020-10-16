# Computational-Thinking-Code

##Project Title
Hangman Project

import random

## This function selects a random word from an imported txt file
def get_word():
    f = open("wlist_match11.txt", "r") ##opens and reads the text file
    words = f.readlines()
    f.close() ##close the text file
    listOfWord =[]
    ##this is used to clean up the words from the imported text file
    ##by stripping the right side of the word
    for line in words:
        listOfWord.append(line.rstrip('\n'))
    return random.choice(listOfWord) ##returns a random word from the list


 Utilities2.py

## This function is used to start the actual game itself
def play_hangman():
    word = get_word()## call the get_word function to select a random word
    letters_guessed = []
    WrongLetters =[]
    tries = 8 ##the number of wrong attempts the player gets
    guessed = False
    alphabet = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']
    print('The word contains',len(word), 'letters.')
    print(len(word) * '_ ')
    while guessed == False and tries > 0:
        print('You only have', + tries, 'tries left!')
        guess = input('Please enter one letter or the full word you would like to guess:').lower()
        if len(guess) == 1:
            ##checks to see if the user enters a letter or not.. does not allow special characters
            if guess not in alphabet:
                print('Please enter a letter, no special characters.')
            elif guess in letters_guessed:
                print('You have previously guessed this letter, choose another letter!')
            elif guess not in word:
                print('Sorry, the letter you guessed is not part of the word.')
                WrongLetters.append(guess)
                incorrectLetters(WrongLetters) ##call the incorrectLetters function
                tries -=1
                drawMan(tries) ##Call the drawMan function  
            elif guess in word:
                print('Good guess, this letter is in the word!')
                letters_guessed.append(guess)
            else:
                print('Error')
        #if the player guesses a full word
        elif len(guess) == len(word):
            if guess == word:
                print('Wow! Good work, you guessed the word!')
                guessed = True
            else:
                print('Sorry, that is not the word. Keep playing!')
                tries -= 1
                drawMan(tries)
        else:
            print('Wrong, the word that you guessed does not have the same amount of letters in it as the word you are trying to guess.')
            
        status = ''
        if guessed == False:
            for letter in word:
                if letter in letters_guessed:
                    status += letter
                else:
                    status += '_ '
            print(status)
        
        if status == word:
            print('Awesome! You have guessed the word.')
            guessed = True
        elif tries == 0:
            print('Sorry, you are out of guesses and did not guess the word.')
            print ("The word was:" + word )
 

Utilities3.py

##This function will display the incorrect letters that the user previously attempted to guess
def incorrectLetters(guess):
    print ("The incorrect letters you have guessed are: " +str(guess))


Utilities4.py

##Hangman Board
def drawMan (tries):
    while True:
•	if tries == 7:
            print('    ____')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print(' -----   ')
            tries-=1
            break
        
            
•	if tries == 6:
            print('    ____')
            print('   |   |')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print(' -----   ')
            tries-=1
            break   
        
        
•	if tries == 5:
            print('    ____')
            print('   |   |')
            print('   |   O')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print(' -----   ')
            tries-=1
            break
        
        tries-=1
•	if tries == 4:
            print('    ____')
            print('   |   |')
            print('   |   O')
            print('   |   |')
            print('   |     ')
            print('   |     ')
            print('   |     ')
            print(' -----   ')
            tries-=1
            break
        
        
•	if tries == 3:
            print('    ____')
            print('   |   |')
            print('   |   O')
            print('   |   |')
            print('   |   |')
            print('   |     ')
            print('   |     ')
            print(' -----   ')
            tries-=1
            break
        
        
•	if tries == 2:
            print('    ____')
            print('   |   |')
            print('   |   O')
            print('   |   |')
            print('   |   |')
            print('   | _/')
            print('   |     ')
            print(' -----   ')
            tries-=1
            break
        
        
•	if tries == 1:
            print('    ____')
            print('   |   |')
            print('   |   O')
            print('   |   |')
            print('   |   |')
            print('   | _/ \_')
            print('   |     ')
            print(' -----   ')
            tries -=1
            break
        
        
•	if tries == 0:
            print('    ____')
            print('   |   |')
            print('   |   O')
            print('   |  \|')
            print('   |   |')
            print('   | _/ \_')
            print('   |     ')
            print(' -----   ')
            tries -=1
            break
        
        
•	if tries ==-1:
            print('    ____')
            print('   |   |')
            print('   |   O')
            print('   |  \|/')
            print('   |   |')
            print('   | _/ \_')
            print('   |GAME OVER!')
            print(' -----   ')
            break


