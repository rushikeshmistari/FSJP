import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.ResultSet;
import java.sql.SQLException;
import java.sql.Statement;
import java.util.Scanner;

public class StudentCRUD {
    private static final String URL = "jdbc:mysql://localhost:3306/college";
    private static final String USER = "root";
    private static final String PASSWORD = "your_password";

    public static void main(String[] args) {
        try (Connection con = DriverManager.getConnection(URL, USER, PASSWORD);
             Scanner sc = new Scanner(System.in)) {
            createTable(con);
            while (true) {
                System.out.println("\n1. Insert  2. Update  3. Delete  4. Display  5. Exit");
                System.out.print("Enter choice: ");
                int choice = sc.nextInt();
                switch (choice) {
                    case 1 -> insertStudent(con, sc);
                    case 2 -> updateStudent(con, sc);
                    case 3 -> deleteStudent(con, sc);
                    case 4 -> displayStudents(con);
                    case 5 -> { System.out.println("Program ended."); return; }
                    default -> System.out.println("Invalid choice.");
                }
            }
        } catch (SQLException e) {
            System.out.println("Database error: " + e.getMessage());
        }
    }

    private static void createTable(Connection con) throws SQLException {
        String sql = "CREATE TABLE IF NOT EXISTS students (roll_no INT PRIMARY KEY, name VARCHAR(100) NOT NULL, marks FLOAT NOT NULL)";
        try (Statement st = con.createStatement()) { st.executeUpdate(sql); }
    }

    private static void insertStudent(Connection con, Scanner sc) throws SQLException {
        System.out.print("Roll number: "); int roll = sc.nextInt();
        sc.nextLine();
        System.out.print("Name: "); String name = sc.nextLine();
        System.out.print("Marks: "); float marks = sc.nextFloat();
        String sql = "INSERT INTO students (roll_no, name, marks) VALUES (?, ?, ?)";
        try (PreparedStatement ps = con.prepareStatement(sql)) {
            ps.setInt(1, roll); ps.setString(2, name); ps.setFloat(3, marks);
            System.out.println(ps.executeUpdate() > 0 ? "Student inserted." : "No record inserted.");
        }
    }

    private static void updateStudent(Connection con, Scanner sc) throws SQLException {
        System.out.print("Roll number to update: "); int roll = sc.nextInt();
        sc.nextLine();
        System.out.print("New name: "); String name = sc.nextLine();
        System.out.print("New marks: "); float marks = sc.nextFloat();
        String sql = "UPDATE students SET name = ?, marks = ? WHERE roll_no = ?";
        try (PreparedStatement ps = con.prepareStatement(sql)) {
            ps.setString(1, name); ps.setFloat(2, marks); ps.setInt(3, roll);
            System.out.println(ps.executeUpdate() > 0 ? "Student updated." : "Roll number not found.");
        }
    }

    private static void deleteStudent(Connection con, Scanner sc) throws SQLException {
        System.out.print("Roll number to delete: "); int roll = sc.nextInt();
        try (PreparedStatement ps = con.prepareStatement("DELETE FROM students WHERE roll_no = ?")) {
            ps.setInt(1, roll);
            System.out.println(ps.executeUpdate() > 0 ? "Student deleted." : "Roll number not found.");
        }
    }

    private static void displayStudents(Connection con) throws SQLException {
        String sql = "SELECT roll_no, name, marks FROM students ORDER BY roll_no";
        try (Statement st = con.createStatement(); ResultSet rs = st.executeQuery(sql)) {
            System.out.println("\nRoll No\tName\tMarks");
            while (rs.next()) {
                System.out.println(rs.getInt("roll_no") + "\t" + rs.getString("name") + "\t" + rs.getFloat("marks"));
            }
        }
    }
}
