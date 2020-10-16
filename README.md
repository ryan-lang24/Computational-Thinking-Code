# Computational-Thinking-Code

## Project Title
"Hangman Project"

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

##This utility is used for selecting a word to be used within the game. We imported a text file off of the internet, which consists of 45,000 used English words.  This program sorts through the list of words, and selects one of those words at random.  This becomes the word that the player has to guess during the game.##


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
 
 ##This function is the entirety of the game.  This function takes the selected word from the function above it, and makes that the target for the player to reach.  The len function shows the player the amount of letters that the randomly selected word consists of.  We gave the player the ability to guess a letter from the alphabet, and if they guessed correctly, we gave them a message stating that letter is in the word.  If they guess the wrong letter, we tell them the letter is not in the word through the incorrectLetters function.  After every failed guess attempt, we subtract one try from their number of attempts using our drawMan function.  When the player guesses the correct word or guesses every letter in the word, we give an output message stating that the player has won the game.  If the player attempts to guess the word but fails, we allow the player to continue playing until the user runs out of attempts.  Once the user is out of guesses and fails to discover the word, we produce a statement saying they lost the game and we state what the word was.##
##We have implemented multiple precautions for error handling.  For any special characters or numbers that are typed in, we wanted to produce an error message to limit the guesses to letters only.  Also, we produce an error message for any letter that has been previously guessed in order to prevent tries to be lost over repeat letters.  When the player attempts to guess the complete word, if the guess does not match the length of the word, we want to warn the player that it does not have the same amount of letters.##




## Displaying the incorrect letters
def incorrectLetters(guess):
    print ("The incorrect letters you have guessed are: " +str(guess))

##This function is used to give a letter bank for the user to refer to while playing.  We want to allow the user to know their previous guesses, which can help prevent repeat letters.  Although we have precautions to prevent this error, we want to make our program as user friendly as possible.  We give a letter bank of incorrect letter guesses because the letters that were guessed correctly can be already be seen.##

## Hangman Board
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


