# Tic-Tac-Toe
This is a simple Tic Tac Toe game built by python where you have to input row and column number to fix your spot
board = [["-", "-", "-"],["-", "-", "-"],["-", "-", "-"]]
def showBoard():
    for i in board:
        for j in i:
            print(j,end="")
        print()
def checkSpot(row, col):
    if board[row][col] == "X" or board[row][col] == "O":
        return True
    return False
def fixSpot(row, col, player):
    board[row][col] = player
def winningCheck(player):
    win = False
    n = len(board)
    for i in range(n):
        win = True
        for j in range(n):
            if board[i][j] != player:
                win = False
                break
        if win:
            return win
    for i in range(n):
        win = True
        for j in range(n):
            if board[j][i] != player:
                win = False
                break
        if win:
            return win
    for i in range(n):
        win = True
        if board[i][i] != player:
            win = False
            break
    if win:
        return win
    for i in range(n):
        win = True
        if board[i][n-1-i] != player:
            win = False
            break
    if win:
        return win
    return win
def boardFilled():
    for i in board:
        for j in i:
            if j == "-":
                return False
    return True
def swapPlayerTurn(player):
    return "X" if player == "O" else "O"
player = "X"
while True:
    if player == "X":
        print("Player 1 turn")
    else:
        print("Player 2 turn")
    showBoard()
    r, c = list(map(int, input("Enter row and column, separate your desired two number by one space, to fix your spot:").split()))
    print()
    if checkSpot(r-1,c-1):
        while True:
            print("Spot is already taken")
            if player == "X":
                print("Player 1 turn")
            else:
                print("Player 2 turn")
            showBoard()
            r, c = list(map(int, input("Enter row and column, separate your desired two number by one space, to fix your spot:").split()))
            print()
            if checkSpot(r-1, c-1) == False:
                break
    fixSpot(r-1, c-1, player)
    if winningCheck(player):
        if player == "X":
            print("Player 1 wins!")
            break
        else:
            print("Player 2 wins!")
            break
    if boardFilled():
        print("Match Draw!")
        break
    player = swapPlayerTurn(player)   
showBoard()    
