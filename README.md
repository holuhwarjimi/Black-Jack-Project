# Black-Jack-Project

import random

cards = [11, 2, 3, 4, 5, 6, 7, 8, 9, 10, 10, 10, 10]

def deal_card():
    """Returns a random card from the deck."""
    card = random.choice(cards)
    return card


user_cards = []
computer_cards = []

is_game_over = False

for x in range(2):
    user_cards.append(deal_card())
    
for x in range(2):
    computer_cards.append(deal_card())    


def calculate_score(cards):
    """Takes a list of cards as input, and returns the score"""
    if sum(cards) == 21 and len(cards) == 2:
        return 0
    if 11 in cards and sum(cards) > 21:
        cards.remove(11)
        cards.append(1)
        
    
    return sum(cards)

while is_game_over == False:
    user_score = calculate_score(user_cards)
    computer_score = calculate_score(computer_cards)
    print(f"Your cards are: {user_cards}, and your score is: {user_score}")
    print(f"The computer first card is: {computer_cards[0]}")

    if user_score == 0 or computer_score == 0 or user_score > 21:
        is_game_over = True
    else:
        should_continue = input("Do you want to draw another card? Y or N \n")
        if should_continue == "Y":
            user_cards.append(deal_card())                
        else:
            is_game_over = True
    while computer_score != 0 and computer_score < 17:
        computer_cards.append(deal_card())
        computer_score = calculate_score(computer_cards)


def compare(user_score, computer_score):
    if user_score == computer_score:
        return "It's a draw"
    elif computer_score == 0:
        return "You loose"
    elif user_score == 0:
        return "You win"
    elif user_score > 21: 
        return "You loose"
    elif computer_score > 21:
        return "You win"
    elif computer_score > user_score:
        return "You loose"
    elif user_score > computer_score:
        return "You win"


compare(user_score, computer_score)   
