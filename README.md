# Tic-Tac-Toe
import random 

board = ["-", "-", "-",
         "-", "-", "-",
         "-", "-", "-"]

player = "X"
winner = None
game = True

def printBoard(board):
    print(board[0] + "|" + board[1] + "|" + board[2])
    print("-" * 7)
    print(board[3] + "|" + board[4] + "|" + board[5])
    print("-" * 7)
    print(board[6] + "|" + board[7] + "|" + board[8])

def playerinput(board):
    a = int(input("Enter a number from 0-8: "))
    if 0 <= a <= 8 and board[a] == "-":
        board[a] = player
    elif a>8:
      print("doesn't exist")
    else:
        print("This place is already taken.")

def switch_player(board):
  player="O"
  playerinput(board)

def checkwinwin(board):
    global winner
    if board[0]==board[1]==board[2] and board[0]!="-":
        winner= board[0]
        return True
    elif board[3]==board[4]==board[5] and board[3]!="-" :
       winner= board[3]
       return True
    elif board[6]==board[7]==board[8] and board[6]!="-" :
       winner=board[6]
       return True


    if board[0]==board[3]==board[6] and board[0]!="-":
        winner= board[0]
        return True
    elif board[1]==board[4]==board[7] and board[1]!="-" :
       winner= board[1]
       return True
    elif board[2]==board[5]==board[8] and board[2]!="-" :
       winner=board[2]
       return True


    if board[0]==board[4]==board[8] and board[0]!="-":
         winner= board[0]
         return True
    elif board[2]==board[4]==board[6] and board[2]!="-" :
       winner= board[2]
       return True

def checktie(board):
     global game
     if "-" not in board:
      printBoard(board)
      print("Tie")
      game=False
def switchplayer():
  global player
  if player== "X":
    player= "O"
  else:
    player= "X"
def whoisthewinner():
  global game
  if checkwinwin(board):
    print(f"Winner: {winner}")
    game=False

def computer(board):
 while player== "O" :
  position= random.randint(0,8)
  if board[position]== "-" :
    board[position]= "O"
    switchplayer()

while game== True:
    printBoard(board)
    playerinput(board)
    whoisthewinner()
    checktie(board)
    switchplayer()
    computer(board)
    whoisthewinner()
    checktie(board)
