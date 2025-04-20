public class MathOperation {
    // Static constant variable
    public static final double PI = 3.14159;

    // Method to multiply two real numbers
    public static double mul(double a, double b) {
        return a * b;
    }

    // Method to divide two real numbers
    public static double div(double a, double b) {
        if (b == 0) {
            throw new ArithmeticException("Cannot divide by zero.");
        }
        return a / b;
    }
}
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        // Taking user input
        System.out.print("Enter first number: ");
        double num1 = scanner.nextDouble();

        System.out.print("Enter second number: ");
        double num2 = scanner.nextDouble();

        // Performing operations
        double product = MathOperation.mul(num1, num2);
        double quotient = 0;

        try {
            quotient = MathOperation.div(num1, num2);
        } catch (ArithmeticException e) {
            System.out.println(e.getMessage());
        }

        // Output
        System.out.println("PI = " + MathOperation.PI);
        System.out.println("Multiplication: " + product);
        if (num2 != 0) {
            System.out.println("Division: " + quotient);
        }

        scanner.close();
    }
}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

public class MyQueue {
    private int[] queue;
    private int front, rear, size;

    // Constructor
    public MyQueue(int capacity) {
        queue = new int[capacity];
        front = 0;
        rear = -1;
        size = 0;
    }

    // Insert element into queue
    public void insert(int value) {
        if (size == queue.length) {
            System.out.println("Queue is full!");
            return;
        }
        rear = (rear + 1) % queue.length;
        queue[rear] = value;
        size++;
    }

    // Delete element from queue
    public int delete() {
        if (size == 0) {
            System.out.println("Queue is empty!");
            return -1;
        }
        int deleted = queue[front];
        front = (front + 1) % queue.length;
        size--;
        return deleted;
    }

    // Display current queue
    public void display() {
        if (size == 0) {
            System.out.println("Queue is empty!");
            return;
        }
        System.out.print("Queue: ");
        for (int i = 0; i < size; i++) {
            System.out.print(queue[(front + i) % queue.length] + " ");
        }
        System.out.println();
    }
}
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter queue size: ");
        int n = sc.nextInt();

        MyQueue q = new MyQueue(n);

        while (true) {
            System.out.println("\n1. Insert");
            System.out.println("2. Delete");
            System.out.println("3. Display");
            System.out.println("4. Exit");
            System.out.print("Enter choice: ");
            int choice = sc.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter number to insert: ");
                    int val = sc.nextInt();
                    q.insert(val);
                    break;
                case 2:
                    int deleted = q.delete();
                    if (deleted != -1) {
                        System.out.println("Deleted: " + deleted);
                    }
                    break;
                case 3:
                    q.display();
                    break;
                case 4:
                    System.out.println("Exiting...");
                    sc.close();
                    return;
                default:
                    System.out.println("Invalid choice!");
            }
        }
    }
}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

public class MyClass {

    // abs method for int
    public int abs(int x) {
        return (x < 0) ? -x : x;
    }

    // abs method for double
    public double abs(double x) {
        return (x < 0) ? -x : x;
    }

    // abs method for float
    public float abs(float x) {
        return (x < 0) ? -x : x;
    }
}
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        MyClass obj = new MyClass();

        System.out.print("Enter an integer: ");
        int intInput = sc.nextInt();
        System.out.println("Absolute value (int): " + obj.abs(intInput));

        System.out.print("Enter a double: ");
        double doubleInput = sc.nextDouble();
        System.out.println("Absolute value (double): " + obj.abs(doubleInput));

        System.out.print("Enter a float: ");
        float floatInput = sc.nextFloat();
        System.out.println("Absolute value (float): " + obj.abs(floatInput));

        sc.close();
    }
}

