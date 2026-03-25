import random

# Snakes and Ladders positions
snakes = {
    99: 10,
    95: 56,
    92: 48,
    74: 32,
    64: 36,
    62: 19,
    46: 25,
    16: 6
}

ladders = {
    2: 38,
    7: 14,
    8: 31,
    15: 26,
    21: 42,
    28: 84,
    36: 44,
    51: 67,
    71: 91,
    78: 98,
    87: 94
}

# Player positions
player1 = 0
player2 = 0

def roll_dice():
    return random.randint(1, 6)

def move_player(position, dice):
    position += dice
    if position > 100:
        return position - dice  # stay in same place if >100
    
    # Check ladder
    if position in ladders:
        print("🎉 Ladder! Climb up!")
        position = ladders[position]
    
    # Check snake
    elif position in snakes:
        print("🐍 Snake! Go down!")
        position = snakes[position]
    
    return position

# Game loop
while True:
    input("\nPlayer 1 - Press Enter to roll dice...")
    dice = roll_dice()
    print("Player 1 rolled:", dice)
    player1 = move_player(player1, dice)
    print("Player 1 position:", player1)
    
    if player1 == 100:
        print("🏆 Player 1 Wins!")
        break

    input("\nPlayer 2 - Press Enter to roll dice...")
    dice = roll_dice()
    print("Player 2 rolled:", dice)
    player2 = move_player(player2, dice)
    print("Player 2 position:", player2)
    
    if player2 == 100:
        print("🏆 Player 2 Wins!")
        break
