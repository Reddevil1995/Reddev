# Reddev
field = list(range(1,10))
def g_field(field):
    for i in range(3):
        print("|", field[0 + i * 3], "|", field[1 + i * 3], "|", field[2 + i * 3], "|")
        print("_____________")

def chz_input(player_tok):
	valid = False
	while not valid:
		pl_turn = input("Kuda " + player_tok+"? ")
		pl_turn = int(pl_turn)
		if pl_turn >= 1 and pl_turn <= 9:
			if (str(field[pl_turn-1]) not in "XO"):
				field[pl_turn-1] = player_tok
				valid = True
			else:
				print("Zanyato")
		else:
			print("Nepravilno")
def check_win(board):
	win_coord = ((0,1,2),(3,4,5),(6,7,8),(0,3,6),(1,4,7),(2,5,8),(0,4,8),(2,4,6))
	for each in win_coord:
		if board[each[0]] == board[each[1]] == board[each[2]]:
			return board[each[0]]
	return False

def main(field):
	counter = 0
	win = False
	while not win:
		g_field(field)
		if counter % 2 == 0:
			chz_input("X")
		else:
			chz_input("O")
		counter += 1
		if counter > 4:
			b2b = check_win(field)
			if b2b:
				print(b2b, "pobeda")
				win = True
				break
		if counter == 9:
			print("Ничья")
			break
	g_field(field)
main(field)
