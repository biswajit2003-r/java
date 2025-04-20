-------------------------------------------------------DAY 3--------------------------------------------------------------------
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
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------DAY 4-------------------------------------------------------------------------------------
import java.util.Scanner;

abstract class ThreeDObject {
    protected double dim1, dim2, dim3;

    // Abstract methods to calculate surface area and volume
    public abstract double wholeSurfaceArea();
    public abstract double volume();
}

class Box extends ThreeDObject {

    public Box(double length, double breadth, double height) {
        dim1 = length;
        dim2 = breadth;
        dim3 = height;
    }

    // Overridden method to calculate surface area of a box
    public double wholeSurfaceArea() {
        return 2 * (dim1 * dim2 + dim2 * dim3 + dim3 * dim1);
    }

    // Overridden method to calculate volume of a box
    public double volume() {
        return dim1 * dim2 * dim3;
    }
}

class Cube extends ThreeDObject {

    public Cube(double side) {
        dim1 = dim2 = dim3 = side;  // All dimensions are the same for a cube
    }

    // Overridden method to calculate surface area of a cube
    public double wholeSurfaceArea() {
        return 6 * dim1 * dim1;  // Surface area = 6 * side^2
    }

    // Overridden method to calculate volume of a cube
    public double volume() {
        return dim1 * dim1 * dim1;  // Volume = side^3
    }
}

class Cylinder extends ThreeDObject {

    public Cylinder(double radius, double height) {
        dim1 = radius;
        dim2 = height;
    }

    // Overridden method to calculate surface area of a cylinder
    public double wholeSurfaceArea() {
        return 2 * Math.PI * dim1 * (dim1 + dim2);  // Surface area = 2πr(r + h)
    }

    // Overridden method to calculate volume of a cylinder
    public double volume() {
        return Math.PI * dim1 * dim1 * dim2;  // Volume = πr^2h
    }
}

class Cone extends ThreeDObject {

    public Cone(double radius, double height) {
        dim1 = radius;
        dim2 = height;
    }

    // Overridden method to calculate surface area of a cone
    public double wholeSurfaceArea() {
        double slantHeight = Math.sqrt(dim1 * dim1 + dim2 * dim2);  // Slant height = √(r^2 + h^2)
        return Math.PI * dim1 * (dim1 + slantHeight);  // Surface area = πr(r + slant height)
    }

    // Overridden method to calculate volume of a cone
    public double volume() {
        return (1.0 / 3) * Math.PI * dim1 * dim1 * dim2;  // Volume = (1/3)πr^2h
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Box
        System.out.println("Enter length, breadth and height of the Box:");
        double l = sc.nextDouble(), b = sc.nextDouble(), h = sc.nextDouble();
        Box box = new Box(l, b, h);
        System.out.println("Box Surface Area: " + box.wholeSurfaceArea());
        System.out.println("Box Volume: " + box.volume());

        // Cube
        System.out.print("\nEnter side of the Cube: ");
        double side = sc.nextDouble();
        Cube cube = new Cube(side);
        System.out.println("Cube Surface Area: " + cube.wholeSurfaceArea());
        System.out.println("Cube Volume: " + cube.volume());

        // Cylinder
        System.out.print("\nEnter radius and height of the Cylinder: ");
        double r1 = sc.nextDouble(), h1 = sc.nextDouble();
        Cylinder cylinder = new Cylinder(r1, h1);
        System.out.println("Cylinder Surface Area: " + cylinder.wholeSurfaceArea());
        System.out.println("Cylinder Volume: " + cylinder.volume());

        // Cone
        System.out.print("\nEnter radius and height of the Cone: ");
        double r2 = sc.nextDouble(), h2 = sc.nextDouble();
        Cone cone = new Cone(r2, h2);
        System.out.println("Cone Surface Area: " + cone.wholeSurfaceArea());
        System.out.println("Cone Volume: " + cone.volume());

        sc.close();
    }
}
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
import java.util.Scanner;

// Interface Department
interface Department {
    String depName = "Computer Science";  // Department Name
    String depHead = "Dr. Smith";         // Department Head

    // Abstract methods for getting and printing data
    void getData();
    void printData();
}

// Class Hostel
class Hostel {
    protected String hostelName;
    protected String hostelLocation;
    protected int noOfRooms;

    // Method to get hostel data
    public void getHostelData(String hostelName, String hostelLocation, int noOfRooms) {
        this.hostelName = hostelName;
        this.hostelLocation = hostelLocation;
        this.noOfRooms = noOfRooms;
    }

    // Method to print hostel data
    public void printHostelData() {
        System.out.println("Hostel Name: " + hostelName);
        System.out.println("Hostel Location: " + hostelLocation);
        System.out.println("Number of Rooms: " + noOfRooms);
    }
}

// Class Student extends Hostel and implements Department
class Student extends Hostel implements Department {
    private String studentName;
    private String regNo;
    private String electiveSubject;
    private double avgMarks;

    // Constructor to get all data including student data, hostel data, and department data
    public void getData() {
        Scanner sc = new Scanner(System.in);
        
        // Get hostel data
        System.out.print("Enter Hostel Name: ");
        hostelName = sc.nextLine();
        System.out.print("Enter Hostel Location: ");
        hostelLocation = sc.nextLine();
        System.out.print("Enter Number of Rooms in Hostel: ");
        noOfRooms = sc.nextInt();
        
        // Get student data
        sc.nextLine();  // Consume newline
        System.out.print("Enter Student Name: ");
        studentName = sc.nextLine();
        System.out.print("Enter Registration Number: ");
        regNo = sc.nextLine();
        System.out.print("Enter Elective Subject: ");
        electiveSubject = sc.nextLine();
        System.out.print("Enter Average Marks: ");
        avgMarks = sc.nextDouble();
        
        // Department data (interface variables)
        System.out.println("Department Name: " + depName);
        System.out.println("Department Head: " + depHead);
    }

    // Method to print student, hostel, and department data
    public void printData() {
        System.out.println("\n--- Student Information ---");
        System.out.println("Student Name: " + studentName);
        System.out.println("Registration Number: " + regNo);
        System.out.println("Elective Subject: " + electiveSubject);
        System.out.println("Average Marks: " + avgMarks);

        // Print hostel data
        printHostelData();

        // Print department data
        System.out.println("Department Name: " + depName);
        System.out.println("Department Head: " + depHead);
    }
}

// Driver class
public class Main {
    public static void main(String[] args) {
        Student student = new Student();
        
        // Get data from user and print it
        student.getData();
        student.printData();
    }
}
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------

