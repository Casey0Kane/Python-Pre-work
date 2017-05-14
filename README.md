# Python-Pre-work
code 401 pre work from codeacadamy.


# Unit 3 part 10
pyg = 'ay'
original = raw_input('Enter a word:')
if len(original) > 0 and original.isalpha():
   word = original.lower()
   first = word[0]
   new_word = word + first + pyg
   new_word = new_word[1:len(new_word)]
   print new_word
else:
    print 'empty'


# Unit 4 part 7
def hotel_cost(nights):
    return 140 * nights
def plane_ride_cost(city):
    if city == "Charlotte":
        return 183
    elif city == "Tampa":
        return 220
    elif city == "Pittsburgh":
        return 222
    elif city == "Los Angeles":
        return 475
def rental_car_cost(days):
    cost = days*40
    if days >= 7:
        return cost-50    
    elif days >= 3:
        return cost-20
    else:
        return cost
def spending_money(money):
    money = 50*days
        
def trip_cost(city, days, money):
    return rental_car_cost(days) + hotel_cost(days) + plane_ride_cost(city) + money
print trip_cost("Los Angeles", 5, 600)


# Unit 5 part 12
shopping_list = ["banana", "orange", "apple"]

stock = {
    "banana": 6,
    "apple": 0,
    "orange": 32,
    "pear": 15
}
    
prices = {
    "banana": 4,
    "apple": 2,
    "orange": 1.5,
    "pear": 3
}

# Write your code below!
def compute_bill(food):
    total =0
    for item in food:
        if stock[item] > 0:
            total += prices[item]
            stock[item] -= 1
    return total


# Unit 6 part 9
lloyd = {
    "name": "Lloyd",
    "homework": [90.0, 97.0, 75.0, 92.0],
    "quizzes": [88.0, 40.0, 94.0],
    "tests": [75.0, 90.0]
}
alice = {
    "name": "Alice",
    "homework": [100.0, 92.0, 98.0, 100.0],
    "quizzes": [82.0, 83.0, 91.0],
    "tests": [89.0, 97.0]
}
tyler = {
    "name": "Tyler",
    "homework": [0.0, 87.0, 75.0, 22.0],
    "quizzes": [0.0, 75.0, 78.0],
    "tests": [100.0, 100.0]
}

# Add your function below!
def average(numbers):
    total = sum(numbers)
    total = float(total)
    total = total / len(numbers)
    return total
def get_average(student):
    h = average(student["homework"])
    q = average(student["quizzes"])
    t = average(student["tests"])
    aver = (h * 0.1) + (q * 0.3) + (t * 0.6)
    return aver
students = [lloyd, alice, tyler]

def get_class_average(classlist):
    results=[]
    for student in classlist:
        result = get_average(student)
        results.append(result)
    return average(results)

def get_letter_grade(score):
    if score >= 90:
        return "A"
    elif score >= 80 and score < 90:
        return "B"
    elif score >= 70 and score < 80:
        return "C"
    elif score >= 60 and score < 70:
        return "D"
    else:
        return "F"

print get_class_average(students)
print get_letter_grade(get_class_average(students))


# Unit 7 part 18
from random import randint

board = []

for x in range(5):
    board.append(["O"] * 5)

def print_board(board):
    for row in board:
        print " ".join(row)

print "Let's play Battleship!"
print_board(board)

def random_row(board):
    return randint(0, len(board) - 1)

def random_col(board):
    return randint(0, len(board[0]) - 1)

ship_row = random_row(board)
ship_col = random_col(board)
print ship_row
print ship_col

# Everything from here on should go in your for loop!
# Be sure to indent four spaces!
for turn in range(4):
    print "Turn", turn + 1

    guess_row = int(raw_input("Guess Row:"))
    guess_col = int(raw_input("Guess Col:"))

    if guess_row == ship_row and guess_col == ship_col:
        print "Congratulations! You sunk my battleship!"
        break
    else:
        if (guess_row < 0 or guess_row > 4) or (guess_col < 0 or guess_col > 4):
            print "Oops, that's not even in the ocean."
        elif(board[guess_row][guess_col] == "X"):
            print "You guessed that one already."
        else:
            print "You missed my battleship!"
            board[guess_row][guess_col] = "X"
        if (turn==3 and board[guess_row][guess_col] == "X"):
            print "Game Over"

        print_board(board)