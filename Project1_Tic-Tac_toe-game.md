~~~
board = [' '] * 10

from IPython.display import clear_output

def display_board(board):
    clear_output()
    print('_________')
    print(board[7] + ' | ' + board[8] + ' | ' + board[9])
    print('---------')
    print(board[4] + ' | ' + board[5] + ' | ' + board[6])
    print('---------')
    print(board[1] + ' | ' + board[2] + ' | ' + board[3])
    print('_________')


def player_input():
    marker=''
    while marker!='X' and marker!='O':
    #while marker not in ['X','O']:
        marker = input('Player 1, choose X or O: ').upper()
    if marker=='X':
        return ('X','O')
    else:
        return ('O','X')


def place_marker(board, marker, position):
    board[position] = marker


def win_check(board, mark):
    return ((board[7] == mark and board[8] == mark and board[9] == mark) or # across the top
    (board[4] == mark and board[5] == mark and board[6] == mark) or # across the middle
    (board[1] == mark and board[2] == mark and board[3] == mark) or # across the bottom
    (board[7] == mark and board[4] == mark and board[1] == mark) or # down the middle
    (board[8] == mark and board[5] == mark and board[2] == mark) or # down the middle
    (board[9] == mark and board[6] == mark and board[3] == mark) or # down the right side
    (board[7] == mark and board[5] == mark and board[3] == mark) or # diagonal
    (board[9] == mark and board[5] == mark and board[1] == mark)) # diagonal


import random
def choose_first():
    if random.randint(0,1)==0:
        return 'Player 2'
    else:
        return 'Player 1'


def space_check(board, position):
    return board[position]==' '


def full_board_check(board):
    for i in range(1,10):
        if space_check(board, i):
            return False
    return True


def player_choice(board):
    position = 0
    while position not in [1,2,3,4,5,6,7,8,9] or not space_check(board, position):
        position = int(input('Choose from 1-9: '))
    return position


board = [' '] * 10
turn = choose_first()
print(f'{turn} goes first')
player_m1, player_m2 = player_input()

game_on = True
while game_on:
    if turn=='Player 1':
        display_board(board)
        print(f'{turn} choose your position')
        position = player_choice(board)
        place_marker(board, player_m1, position)
        if win_check(board, player_m1):
            display_board(board)
            print(f'Congratulations Player 1, you have won!')
            game_on = False
        else:
            if full_board_check(board):
                display_board(board)
                print('The game is draw!')
                break
            else:
                turn = 'Player 2'
    else:
        display_board(board)
        print(f'{turn} choose your position')
        position = player_choice(board)
        place_marker(board, player_m2, position)
        if win_check(board, player_m2):
            print(f'Congratulations Player 2, you have won!')
            break
        else:
            if full_board_check(board):
                display_board(board)
                print('The game is draw!')
                break
            else:
                turn = 'Player 1'
~~~
