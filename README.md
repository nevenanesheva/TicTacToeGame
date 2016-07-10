# TicTacToeGame
Tic Tac Toe Game  
public class Player {
	String name;
	char symbol;
	
	//constructor for creating an object from class Player
	Player(String name, char symbol){
		if(name != null && !(name.isEmpty())){
			this.name = name;
		}
		
		if(symbol == 'x' || symbol == 'o'){
			this.symbol = symbol;
		}
		
		else{
			System.out.println(this.name + " has choosen incorrect symbol!");
			System.out.println("Please, try again!");
		}
	}
	
	
	void showPlayerInfo(){
		System.out.println("     PLAYER'S INFO     ");
		System.out.println(" *********************************");
		System.out.println("  Name: " + this.name);
		System.out.println("  Choosen symbol for playing: " + this.symbol);
		System.out.println(" *********************************");
		System.out.println();
	}

}


public class Board {
	Scanner sc = new Scanner(System.in);
	
	char[][] board = new char[3][3];
	
	//method for setting a position on the board
	void setPosition(Player player){
		System.out.println("Now, it's your time! Enter a position: ");
		int row = sc.nextInt();
		int col = sc.nextInt();
		if(row >= board.length || col >= board.length){
			System.out.println("Incorrect position choosen!");
		}
		board[row][col] = player.symbol;
	}
	
	//method for displaying the board
	void displayBoard(){
		System.out.println();
		System.out.println("BOARD LOOKS LIKE");
		System.out.println();
		System.out.println(" - - - - - - ");
		System.out.println("| " + board[0][0] + " | " + board[0][1] + " | " + board[0][2] + " |");
		System.out.println(" - - - - - - ");
		System.out.println("| " + board[1][0] + " | " + board[1][1] + " | " + board[1][2] + " |");
		System.out.println(" - - - - - - ");
		System.out.println("| " + board[2][0] + " | " + board[2][1] + " | " + board[2][2] + " |");
		System.out.println(" - - - - - - ");
		
		System.out.println();
		//System.out.println("Let's continue playing! :)");
		System.out.println();
	}
	
	public boolean isSomebodyWins(char[][] board, char player){
	
		boolean win = false;
		if (board[0][0] == player && board[0][1] == player && board[0][2] == player ||
	            board[1][0] == player && board[1][1] == player && board[1][2] == player || 
	            board[2][0] == player && board[2][1] == player && board[2][2] == player || 
	            board[0][0] == player && board[1][0] == player && board[2][0] == player || 
	            board[0][1] == player && board[1][1] == player && board[2][1] == player || 
	            board[0][2] == player && board[1][2] == player && board[2][2] == player ||
	            board[0][0] == player && board[1][1] == player && board[2][2] == player ||           
	            board[2][0] == player && board[1][1] == player && board[0][2] == player){
			win = true;
		}
		
		else{
			win = false;
		}

	    
			return win;
		}
	
}


public class GameDemo {

	public static void main(String[] args) {
		// TODO Auto-generated method stub
		
		System.out.println("------------------------------------------------------------");
		System.out.println("*****  *    **     *****    *      **     *****   **   *****");
		System.out.println("  *    *  *          *    *****  *          *    *  *  *****");
		System.out.println("  *    *    **       *   *     *   **       *     **   *****");
		System.out.println("------------------------------------------------------------");
		System.out.println();
		System.out.println();
		
		System.out.println("DEAR PLAYERS, YOUR BOARD HAS THESE CORDINATES: ");
		System.out.println(" - - - - - - - - - ");
		System.out.println("| " + "0 0" + " | " + "0 1" + " | " + "0 2" + " |");
		System.out.println(" - - - - - - - - - ");
		System.out.println("| " + "1 0" + " | " + "1 1" + " | " + "1 2" + " |");
		System.out.println(" - - - - - - - - - ");
		System.out.println("| " + "2 0" + " | " + "2 1" + " | " + "2 2" + " |");
		System.out.println(" - - - - - - - - - ");
		System.out.println();
		System.out.println();
		
		System.out.println("While playing, you have to enter them, in case you want to point a position on the board.");
		System.out.println();
		System.out.println("The player who succeeds in placing three of their marks in a horizontal, vertical, or diagonal row wins the game.");
		System.out.println();
		System.out.println();
		
		//creating our players
		Player first = new Player("Maria", 'x');
		Player second = new Player("Ivan", 'o');
		
		first.showPlayerInfo();
		second.showPlayerInfo();
		System.out.println();
		
		Board game = new Board();
		
		boolean winner = false;
		
		for(int i = 1; i <= 5; i++){
			game.setPosition(first);
			game.setPosition(second);
			game.displayBoard();
			
			if(game.isSomebodyWins(game.board, first.symbol) || game.isSomebodyWins(game.board, second.symbol)){
				winner = true;
				break;
			}
			
		}
		
		if(winner){
			System.out.println("We have a winner!");
			if(game.isSomebodyWins(game.board, 'x')){
				System.out.println("Symbol-winner: x");
				if(first.symbol == 'x'){
					System.out.println("Congratulations to " + first.name);
				}
			}
			
			else{
				System.out.println(" ---------------------------------------");
				System.out.println(" Symbol-winner: o                      ");
				System.out.println(" Congratulations to " + second.name + "!");
				System.out.println(" ---------------------------------------");
			}
			
		}
		
		else{
			System.out.println("No winner!");
		}
		
		System.out.println(" ------------------------------------------------------------- ");
		System.out.println("   ***      *    *     *  *****     **   *   *  *****  *****");
		System.out.println("  *   **  *****  *  *  *  *****    *  *   * *   *****  ***");
		System.out.println("   * *   *     * *     *  *****     **     *    *****  *    *");
		System.out.println(" -------------------------------------------------------------");
		
	}
	
	
}
