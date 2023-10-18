# Codesoft

import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int min = 1;
        int max = 100;
        int numberOfAttempts = 5;
        int score = 0;

        boolean playAgain = true;
        while (playAgain) {
            int generatedNumber = random.nextInt(max - min + 1) + min;
            int attempts = 0;

            System.out.println("Welcome to the Number Guessing Game!");
            System.out.println("A random number between " + min + " and " + max + " has been generated.");

            boolean guessedCorrectly = false;
            while (!guessedCorrectly && attempts < numberOfAttempts) {
                System.out.print("Enter your guess: ");
                int userGuess = scanner.nextInt();

                if (userGuess == generatedNumber) {
                    System.out.println("Congratulations! You guessed the correct number.");
                    guessedCorrectly = true;
                    score++;
                } else if (userGuess < generatedNumber) {
                    System.out.println("Too low! Try again.");
                } else {
                    System.out.println("Too high! Try again.");
                }

                attempts++;
            }

            if (!guessedCorrectly) {
                System.out.println("Sorry, you are out of attempts. The correct number was: " + generatedNumber);
            }

            System.out.print("Do you want to play again? (yes/no): ");
            String playAgainOption = scanner.next();
            if (!playAgainOption.equalsIgnoreCase("yes")) {
                playAgain = false;
            }
        }

        System.out.println("Game over! Your final score is: " + score);
        scanner.close();
    }
}
