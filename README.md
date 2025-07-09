//guess the number :
import java.util.Scanner;
import java.util.Random;

public class Main {

    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        Random r = new Random();
        int l = 1;
        int u = 100;
        int maxAttempts = 5;
        int score = 0;
        int round = 1;
        System.out.print("Guess a number between " + l+ " and " + u+ ": ");
        boolean play = true;
        while (play) {
            System.out.println("Round " + round);
            int Guess = r.nextInt(u- l + 1) + l;
            int attemptsLeft = maxAttempts;
            boolean guessedCorrect= false;

            while (attemptsLeft > 0) {
                System.out.print("Enter your guess (" + attemptsLeft + " attempts left): ");

                if (!s.hasNextInt()) {
                    System.out.println("Invalid input. Please enter a number.");
                    s.next();
                    continue;
                }

                int guess = s.nextInt();

                if (guess < Guess) {
                    System.out.println("📉 Too low!");
                } else if (guess > Guess) {
                    System.out.println("📈 Too high!");
                } else {
                    System.out.println("🎉 Correct! You guessed the number!");
                    guessedCorrect= true;
                    score++;
                    break;
                }

                attemptsLeft--;
            }

            if (!guessedCorrect) {
                System.out.println(" You've run out of attempts. The correct number was " +Guess + ".");
            }

            System.out.println("Current Score: " + score + " win(s)");

            System.out.print("Do you want to play another round? (yes/no): ");
            s.nextLine();
            String response = s.nextLine().trim().toLowerCase();
            play = response.equals("yes") || response.equals("y");
            round++;
        }

        System.out.println("\n🎮 Game Over!");
        System.out.println("Total Rounds Played: " + (round - 1));
        System.out.println("Total Wins: " + score);
        s.close();
    }
}
