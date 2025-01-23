# CodeAlpha_Project_Name.
package codealpha1;
import java.util.Scanner;
public class Gradetracker {

	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
       System.out.println("welcome to my codealpha project");
        // Array to store grades as percentages (maximum 100 students)
        int[] grades = new int[100];
        int numStudents = 0;

        while (true) {
            System.out.print("Enter percentage for Student " + (numStudents + 1) + " (0-100) or 'stop' to exit: ");
            String input = scanner.nextLine();

            // If user types "stop", exit the loop
            if (input.equalsIgnoreCase("stop")) {
                break;
            }

            try {
                int percentage = Integer.parseInt(input);

                if (percentage >= 0 && percentage <= 100) {
                    grades[numStudents] = percentage;
                    numStudents++;
                } else {
                    System.out.println("Invalid percentage. Please enter a value between 0 and 100.");
                }
            } catch (NumberFormatException e) {
                System.out.println("Invalid input. Please enter a valid percentage (0-100) or 'stop' to exit.");
            }

            if (numStudents == 100) {
                System.out.println("Maximum number of students reached.");
                break;
            }
        }

        if (numStudents == 0) {
            System.out.println("No grades entered. Exiting program.");
            scanner.close();
            return;
        }

        // Find highest and lowest grades
        int highestGrade = grades[0];
        int lowestGrade = grades[0];

        for (int i = 1; i < numStudents; i++) {
            if (grades[i] < highestGrade) {
                highestGrade = grades[i]; // Lower percentage = Higher grade
            }
            if (grades[i] > lowestGrade) {
                lowestGrade = grades[i]; // Higher percentage = Lower grade
            }
        }
        System.out.println("\nGrades Entered:");
        for (int i = 0; i < numStudents; i++) {
            System.out.println("Student " + (i + 1) + ": " + grades[i] + "% (" + percentageToGrade(grades[i]) + ")");
        }
        System.out.println("\nHighest Grade: " + highestGrade + "% (" + percentageToGrade(highestGrade) + ")");
        System.out.println("Lowest Grade: " + lowestGrade + "% (" + percentageToGrade(lowestGrade) + ")");

        scanner.close();
    }

    public static String percentageToGrade(int percentage) {
        if (percentage >= 90) {
            return "A";
        } else if (percentage >= 80) {
            return "B";
        } else if (percentage >= 70) {
            return "C";
        } else if (percentage >= 60) {
            return "D";
        } else {
            return "F";
        }
    }
}
