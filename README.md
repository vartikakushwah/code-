import java.util.Random;
import javax.swing.JOptionPane;
 
public class NumberGuessing{
    public static void main(String[] args) {
        int rStrt = 1, rEnd = 100, maxAtt = 4, score = 0, rounds = 0;
        boolean play = true;
 
        while (play) {
            rounds++;
            Random random = new Random();
            int randomNumber = random.nextInt(rEnd - rStrt + 1) + rStrt;
            int attempts = 0;
            boolean numGuessed = false;
 
            while (!numGuessed && attempts < maxAtt) {
                String userInput = JOptionPane.showInputDialog(null,
                        "Round " + rounds + ": Guess a number between " + rStrt + " and " + rEnd);
 
                try {
                    int guessnumb = Integer.parseInt(userInput);
                    attempts++;
 
                    if (guessnumb == randomNumber) {
                        numGuessed = true;
                        score += maxAtt - attempts + 1;
                        JOptionPane.showMessageDialog(null, "Congrats! You guessed the correct number.");
                    } else if (guessnumb < randomNumber) {
                        JOptionPane.showMessageDialog(null, "Guess number is too low!:(-- Try again.");
                    } else {
                        JOptionPane.showMessageDialog(null, "Guess number is too high!:(-- Try again.");
                    }
                } catch (NumberFormatException e) {
                    JOptionPane.showMessageDialog(null, "Invalid input data... Please enter a number.");
                }
            }
 
            if (!numGuessed) {
                JOptionPane.showMessageDialog(null, "Out of attempts. The original number was: " + randomNumber);
            }
 
            int playAgain = JOptionPane.showConfirmDialog(null, "Do you want to play again?");
            if (playAgain != JOptionPane.YES_OPTION) {
                play = false;
            }
        }
 
        JOptionPane.showMessageDialog(null, "Game over! Your final score is: " + score + " after " + rounds + " rounds.");
JOptionPane.showMessageDialog(null, "Thanks for playing" );
    }
}
