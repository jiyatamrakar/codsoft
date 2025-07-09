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
//2.student marks calculator :-
class Main{
    public static void main(String[] args) {
        int[] marks=new int[5];
        int totalmarks=0;
        String grade;
        Scanner s = new Scanner(System.in);
        System.out.println("enter your marks at each 5 subjects :-");
        marks[0]=s.nextInt();
        marks[1]=s.nextInt();
        marks[2]=s.nextInt();
        marks[3]=s.nextInt();
        marks[4]=s.nextInt();

        for(int i=0;i<6;i++){
            totalmarks=totalmarks+i;
        }
        int avg=totalmarks/5;
        if(avg>=85){
            grade="A";
        }if(avg>=65&&avg<85){
            grade="B";
        }if(avg>=55&&avg<65){
            grade="C";
        }if(avg>=45&&avg<55){
            grade="D";
        }else{
            grade="FAIL...";
        }
        System.out.println("STUDENT'S RESULT :-");
                System.out.println("TotalMarks : "+totalmarks);
                System.out.println("Average percent : "+avg+"%");
                System.out.println("Grade : "+grade);
    }
}
//3.atm interface :-
class BankAcc {
     double balance;

    public BankAcc(double initialBalance) {
        this.balance = initialBalance;
    }

    public boolean withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            return true;
        }
        return false;
    }

    public boolean deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            return true;
        }
        return false;
    }

    public double getBalance() {
        return balance;
    }
}


class ATM {
    private BankAcc acc;

    public ATM(BankAcc acc) {
        this.acc = acc;
    }

    public void withdraw(double amount) {
        if (acc.withdraw(amount)) {
            System.out.println("Withdrawal successful" + amount + " withdrawn.");
        } else {
            System.out.println("Withdrawal failed! Insufficient balance or invalid amount.");
        }
    }

    public void deposit(double amount) {
        if (acc.deposit(amount)) {
            System.out.println("Deposit successful" + amount + " deposited.");
        } else {
            System.out.println("Deposit failed! Please enter a valid amount.");
        }
    }

    public void checkBalance() {
        System.out.println("Current balance: ₹" + acc.getBalance());
    }
}


public class  Main{
    public static void main(String[] args) {
        Scanner s = new Scanner(System.in);
        BankAcc myAcc = new BankAcc(10000); 
        ATM atm = new ATM(myAcc);

        while (true) {
            System.out.println("WELCOME TO ATM :- ");
            System.out.println("1. Check Balance");
            System.out.println("2. Withdraw");
            System.out.println("3. Deposit");
            System.out.println("4. Exit");
            System.out.print("Choose an option (1-4): ");
            int choice = s.nextInt();

            switch (choice) {
                case 1:
                    atm.checkBalance();
                    break;
                case 2:
                    System.out.print("Enter amount to withdraw: ");
                    double withdrawAmount = s.nextDouble();
                    atm.withdraw(withdrawAmount);
                    break;
                case 3:
                    System.out.print("Enter amount to deposit: ");
                    double depositAmount = s.nextDouble();
                    atm.deposit(depositAmount);
                    break;
                case 4:
                    System.out.println("Thank you for using the ATM. Goodbye!");
                    return;
                default:
                    System.out.println("Invalid choice. Please select a valid option.");
            }
        }
    }
}
