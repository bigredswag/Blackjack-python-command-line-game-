# Blackjack-python-command-line-game-#
#Blackjack in a python command line/console (VERY BEGINNER WILL UPDATE)#
import random
counter = 0
turn = 0

#function of the actual game to run#
def game():
#setting initial values of player's cards#
  card1 = random.randint(1,13)
  card2 = random.randint(1,13)
  card3 = random.randint(1,13)
  card4 = random.randint(1,13)

#setting initial values of dealer's cards#
  dealer1 = random.randint(1,13)
  dealer2 = random.randint(1,13)
  dealer3 = random.randint(1,13)
  dealer4 = random.randint(1,13)
#bank = 100#
  

#function to play another round of blackjack#
  def playAgain():
    newRound = input("Would you like to play again?")
    if(newRound == "yes"):
      game()
    else:
      exit()




#function to display what cards the user has and will have depending on in-game decision#
  def showCards(counter):
    print("First card: " + str(card1))
    print("Second card: " + str(card2))
    if (counter == 1):
      print("Third card: " + str(card3))
    elif (counter == 2):
      print("Third card: " + str(card3))
      print("Fourth card: " + str(card4))

#function to check the sum of the cards of the user, and either continuing or ending the game based on cards#
  def checkSum_User():
    if (sumOfCards > 21):
      print("Game over")
      playAgain()
    elif (sumOfCards == 21):
      print("Winner with blackjack")
      playAgain()

  def checkSum_Dealer():
    if (sumOfDealer > 21):
      print("Dealer busts, player wins")
      playAgain()
    elif (sumOfDealer == 21):
      print("Dealer wins with blackjack")
      playAgain()

#function to compare user and dealer to determine winner#
  def compareValues():
    if (sumOfCards > sumOfDealer):
      print("Player wins")
    elif (sumOfCards < sumOfDealer):
      print("Dealer wins")
    else:
      print("Draw")
  
    playAgain()



#function to display current dealer's cards so user can decide if they want to go on or not#
  def dealer_hand(turn):
    if (turn == 0):
      print("Dealer has: ___ and " + str(dealer2))
    elif (turn == 1):
      print("Dealer has: ___ and " + str(dealer2) + " and " + str(dealer3))
    elif (turn == 2):
      print("Dealer has: ___ and " + str(dealer2) + " and " + str(dealer3) + " and " + str(dealer4))
    


#I STILL NEED TO IMPLEMENT THE USE OF BETTING/USER BANK#

#starting the game off with user input#
  firstTurn = input("Would you like to play? ")

  if (firstTurn == "yes"):
    sumOfCards = card1 + card2
    sumOfDealer = dealer1 + dealer2
    showCards(0)
    print("your total is: " + str(sumOfCards))
    print("")
    checkSum_User()
    dealer_hand(0)
    checkSum_Dealer()
    if (sumOfCards < 21):
    #giving the user the option to continue playing#
      secondTurn = input("continue playing? ")
      if (secondTurn == "yes"):
        sumOfCards = sumOfCards + card3
        sumOfDealer = sumOfDealer + dealer3
        showCards(1)
        print("your total is: " + str(sumOfCards))
        print("")
        checkSum_User()
        dealer_hand(1)
        checkSum_Dealer()
        if (sumOfCards < 21):
        #giving the user the option to continue playing#
          thirdTurn = input("Continue playing? ")
          if (thirdTurn == "yes"):
            sumOfCards = sumOfCards + card4
            sumOfDealer = sumOfDealer + dealer4
            showCards(2)
            print("your total is: " + str(sumOfCards))
            print("")
            checkSum_User()
            dealer_hand(2)
            checkSum_Dealer()
          elif (thirdTurn == "no"):
            print("let's wait for the dealer")
            print("")
            compareValues()
      elif (secondTurn == "no"):
        print("let's wait for the dealer")
        print("")
        compareValues()
  else:
    print("goodbye")
    playAgain()


game()



#IMPLEMENT THE USE OF A BANK IF NECESSARY#
#USE THIS CODE AS A TEMPLATE FOR VB IF NECESSARY#
