class Person {
    String name;
    int age;

    Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}

class Student extends Person {
    String course;
    int rollNumber;

    Student(String name, int age, String course, int rollNumber) {
        super(name, age);
        this.course = course;
        this.rollNumber = rollNumber;
    }
}

class GraduateStudent extends Student {
    int graduationYear;

    GraduateStudent(String name, int age, String course, int rollNumber, int graduationYear) {
        super(name, age, course, rollNumber);
        this.graduationYear = graduationYear;
    }

    void display() {
        System.out.println("Name: " + name);
        System.out.println("Age: " + age);
        System.out.println("Course: " + course);
        System.out.println("Roll Number: " + rollNumber);
        System.out.println("Graduation Year: " + graduationYear);
    }
}

public class MultilevelInheritance {
    public static void main(String[] args) {
        GraduateStudent g = new GraduateStudent("Priya", 22, "MCA", 35, 2027);
        g.display();
    }
}
