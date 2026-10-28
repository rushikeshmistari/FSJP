class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

class Student extends Person {
    int rollNumber;
    String course;

    Student(String name, int age, int rollNumber, String course) {
        super(name, age);
        this.rollNumber = rollNumber;
        this.course = course;
    }

    void display() {
        System.out.println("Student: " + name + ", Age: " + age + ", Roll No: " + rollNumber + ", Course: " + course);
    }
}

class Teacher extends Person {
    String subject;

    Teacher(String name, int age, String subject) {
        super(name, age);
        this.subject = subject;
    }

    void display() {
        System.out.println("Teacher: " + name + ", Age: " + age + ", Subject: " + subject);
    }
}

class Administrator extends Person {
    String department;

    Administrator(String name, int age, String department) {
        super(name, age);
        this.department = department;
    }

    void display() {
        System.out.println("Administrator: " + name + ", Age: " + age + ", Department: " + department);
    }
}

public class HierarchicalInheritance {
    public static void main(String[] args) {
        Student s = new Student("Amit", 19, 10, "Computer Engineering");
        Teacher t = new Teacher("Mehta", 40, "Java Programming");
        Administrator a = new Administrator("Patil", 45, "Academics");
        s.display();
        t.display();
        a.display();
    }
}
