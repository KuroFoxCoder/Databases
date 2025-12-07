```
import java.sql.*;
public class DatabaseManager {
    public static void main(String[] args) throws SQLException, ClassNotFoundException
    {
            Class.forName("com.mysql.cj.jdbc.Driver");
            System.out.println("Driver loaded.");

            Connection connection = DriverManager.getConnection("jdbc:mysql://localhost/miramar","hwuser","Pa$$word");
            System.out.println("Database connected.");
            //Make a statement to execute insertion of new value into Student table
            Statement statement = connection.createStatement();
            statement.executeUpdate("Insert into student(ssn, firstName, middleName, lastName, birthDate, deptID) values('111222333','Philip','David Charles','Collins','1951-01-30','1234');");

            ResultSet resultSet = statement.executeQuery("select * from student where ssn = '111222333';");
            while(resultSet.next())
            {
                System.out.println(resultSet.getString(1) + "\t" + resultSet.getString(2) + "\t" + resultSet.getString(3) + "\t" + resultSet.getString(4) + "\t" + resultSet.getString(5) + "\t" + resultSet.getString(8) + "\t" + resultSet.getString(9));
            }

            statement.executeUpdate("update student set zipCode = '92126' where ssn = '111222333'");
            resultSet = statement.executeQuery("select * from student where ssn = '111222333';");
            while(resultSet.next())
            {
                System.out.println(resultSet.getString(1) + "\t" + resultSet.getString(2) + "\t" + resultSet.getString(3) + "\t" + resultSet.getString(4) + "\t" + resultSet.getString(5) + "\t" + resultSet.getString(8) + "\t" + resultSet.getString(9));
            }
            connection.close();

    }
}
```
