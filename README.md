# number guessing game
import java.util.Random;
import java.util.Scanner;

public class NumberGuessingGame {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Random random = new Random();

        int lowerBound = 1;  // Define the lower bound of the range
        int upperBound = 100;  // Define the upper bound of the range
        int numberToGuess = random.nextInt(upperBound - lowerBound + 1) + lowerBound;
        int attempts = 0;
        int maxAttempts = 5;  // Maximum number of attempts allowed

        System.out.println("Welcome to the Number Guessing Game!");
        System.out.println("I have selected a number between " + lowerBound + " and " + upperBound + ". Can you guess it?");

        while (attempts < maxAttempts) {
            System.out.print("Enter your guess: ");
            int guess = scanner.nextInt();
            attempts++;

            if (guess == numberToGuess) {
                System.out.println("Congratulations! You guessed the number in " + attempts + " attempts.");
                break;
            } else if (guess < numberToGuess) {
                System.out.println("Too low! Try again.");
            } else {
                System.out.println("Too high! Try again.");
            }
        }

        if (attempts >= maxAttempts) {
            System.out.println("Sorry, you've reached the maximum number of attempts. The number was: " + numberToGuess);
        }

        scanner.close();
    }
}
# simple calculator
import java.util.Scanner;

public class SimpleCalculator {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.println("Simple Calculator");
        System.out.print("Enter first number: ");
        double num1 = scanner.nextDouble();

        System.out.print("Enter second number: ");
        double num2 = scanner.nextDouble();

        System.out.println("Select an operation:");
        System.out.println("1: Addition (+)");
        System.out.println("2: Subtraction (-)");
        System.out.println("3: Multiplication (*)");
        System.out.println("4: Division (/)");

        int choice = scanner.nextInt();
        double result = 0;

        switch (choice) {
            case 1:
                result = num1 + num2;
                System.out.println("Result: " + num1 + " + " + num2 + " = " + result);
                break;
            case 2:
                result = num1 - num2;
                System.out.println("Result: " + num1 + " - " + num2 + " = " + result);
                break;
            case 3:
                result = num1 * num2;
                System.out.println("Result: " + num1 + " * " + num2 + " = " + result);
                break;
            case 4:
                if (num2 != 0) {
                    result = num1 / num2;
                    System.out.println("Result: " + num1 + " / " + num2 + " = " + result);
                } else {
                    System.out.println("Error: Division by zero is not allowed.");
                }
                break;
            default:
                System.out.println("Invalid choice. Please select a valid operation.");
                break;
        }

        scanner.close();
    }
}

# online examination
import java.util.Scanner;

public class OnlineExamSystem {
    static Scanner scanner = new Scanner(System.in);
    static String username;
    static String password;

    public static void main(String[] args) {
        login();
        displayMenu();
    }

    static void login() {
        System.out.println("Welcome to the Online Exam System!");
        System.out.print("Enter username: ");
        username = scanner.nextLine();
        System.out.print("Enter password: ");
        password = scanner.nextLine();
        // Validate username and password (you can use a database for this)
        // If validation fails, handle accordingly (e.g., loop back to login)
    }

    static void displayMenu() {
        int choice;
        do {
            System.out.println("\nMain Menu:");
            System.out.println("1. Update Profile and Password");
            System.out.println("2. Start Exam");
            System.out.println("3. Logout");
            System.out.print("Enter your choice: ");
            choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline character

            switch (choice) {
                case 1:
                    updateProfileAndPassword();
                    break;
                case 2:
                    startExam();
                    break;
                case 3:
                    logout();
                    break;
                default:
                    System.out.println("Invalid choice. Please try again.");
            }
        } while (choice != 3);
    }

    static void updateProfileAndPassword() {
        // Implement profile and password update logic
        System.out.println("Profile and Password update feature not implemented in this demo.");
    }

    static void startExam() {
        // Implement exam logic
        System.out.println("Starting exam...");
        // Display questions, timer, handle MCQs selection, auto-submit, etc.
        // Example:
        int totalQuestions = 5;
        int[] answers = new int[totalQuestions]; // Assuming MCQs have 4 options (A, B, C, D)
        for (int i = 0; i < totalQuestions; i++) {
            System.out.println("Question " + (i + 1) + ":");
            System.out.println("A. Option A");
            System.out.println("B. Option B");
            System.out.println("C. Option C");
            System.out.println("D. Option D");
            System.out.print("Your choice (A/B/C/D): ");
            String choice = scanner.nextLine().toUpperCase();
            switch (choice) {
                case "A":
                    answers[i] = 1;
                    break;
                case "B":
                    answers[i] = 2;
                    break;
                case "C":
                    answers[i] = 3;
                    break;
                case "D":
                    answers[i] = 4;
                    break;
                default:
                    System.out.println("Invalid choice. Skipping question.");
                    break;
            }
        }
        // Timer logic (you can use threads for this)
        int examDurationInMinutes = 30;
        int remainingTimeInSeconds = examDurationInMinutes * 60;
        while (remainingTimeInSeconds > 0) {
            System.out.println("Time remaining: " + remainingTimeInSeconds + " seconds");
            // Sleep for 1 second (simulate time ticking)
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            remainingTimeInSeconds--;
        }
        System.out.println("Time's up! Auto-submitting exam...");
        // Submit exam (process answers, calculate score, etc.)
        // Example: displayResults(answers);
        // For demo purposes, we'll just simulate the end of the exam
        System.out.println("Exam submitted successfully.");
        displayMenu(); // Go back to the main menu
    }

    static void logout() {
        System.out.println("Logging out...");
        // Clear session data, reset variables, etc.
        username = null;
        password = null;
        System.out.println("Logged out successfully.");
    }
}
