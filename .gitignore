import com.mysql.cj.protocol.Resultset;

import java.sql.*;
import java.util.*;

public class Project {


    static Connection conn;
    static Statement stmt ;

    public void CreateDatabase() {
        try {
                String sql1 = "CREATE TABLE ORGANISATION(" + "sid VARCHAR(45) NOT NULL," +
                        "O_name VARCHAR(10) NOT NULL," +
                        "email VARCHAR(20) NOT NULL," +
                        "pass VARCHAR(20) NOT NULL," +
                        "PRIMARY KEY (sid))";

                String sql2 = "CREATE TABLE USER(" + "ID VARCHAR(45) NOT NULL," +
                        "NAME VARCHAR(10) NOT NULL," +
                        "OID VARCHAR(45) NOT NULL," +
                          "FOREIGN KEY(OID) REFERENCES ORGANISATION(sid)," +
                        "PRIMARY KEY (ID))";
                stmt = conn.prepareStatement(sql1);
                stmt.executeUpdate(sql1);
                stmt = conn.prepareStatement(sql2);
                stmt.executeUpdate(sql2);
                System.out.println("Now Tables can store data");
        }
        catch (SQLException se) {
            se.printStackTrace();
        }
    }

    public static int Menu()
    {
        int Input;
        Scanner sc1 = new Scanner(System.in);
        System.out.println("1. For Organisation :");
        System.out.println("2. For User Record");
        System.out.println("3. Print Organisation");
        System.out.println("4. Print User record");
        System.out.println("5. Exit from Application");
        System.out.println("Enter your choice :");
        Input = sc1.nextInt();
        return Input;
    }
    public static void OrganisationMenu() {
        try {
        int Input1;
        Scanner sc2 = new Scanner(System.in);
        Project c = new Project();
        do {
        System.out.println("1. Create Organisation :");
        System.out.println("2. Update Organisation");
        System.out.println("3. Remove Organisation");
        System.out.println("4. Press 0 go back to Main menu");
        System.out.println("Enter your choice :");
        Input1=sc2.nextInt();

                switch (Input1) {
                    case 1:
                        c.CreateOrganisationRecord();
                        break;
                    case 2:
                        c.UpdateOrganisation();
                        break;
                    case 3:
                        c.RemoveOrganisation();
                        break;
                    default:
                        System.out.println("Wrong Input");
                }

            }
            while(Input1 != 0);

        }

        catch (Exception e)
        {
            System.out.println(e);
        }

    }
    public void LoginDtabase() {
        try {
            int w = 0;
            do {
                String sql = "select sid,pass from ORGANISATION ";
                stmt = conn.prepareStatement(sql);
                ResultSet rs = stmt.executeQuery(sql);
                Scanner sc = new Scanner(System.in);
                System.out.println("Enter your Organisation ID :");
                String sid = sc.next();
                System.out.println("Enter your password  :");
                String pass =sc.next();
                String i=null;                   
                String j = null;
                while (rs.next()) {
                    i = rs.getString(1);
                    j = rs.getString(2);

                    if ((sid.equals(i)) && (pass.equals(j))) {
                        w++;
                        System.out.println("Login successfully...");
                        CreateUserRecord(sid);

                    } else
                        System.out.println("Login password is wrong");
                }
            }
                while (w == 0) ;


        }
        catch (SQLException se)  {
            se.printStackTrace();
        }

    }
    public void CreateOrganisationRecord() {
        try {
            int sid = 102;
            String want;
            do {
                Scanner sc3 = new Scanner(System.in);
                System.out.println("Enter your Organisation name  :");
                String O_name = sc3.next();
                System.out.println("Enter your Email  :");
                String email = sc3.next();
                System.out.println("Enter your password");
                String pass = sc3.next();
                System.out.println("your login ID :" + sid);
                System.out.println("want you add more record :");
                want = sc3.next();
                if (want.equals("y")) {
                    sid++;
                }

                 String sql="INSERT INTO ORGANISATION(sid,O_name,email,pass)"+"VALUES('"+sid+"','"+O_name+"','"+email+"','"+pass+"');";
               PreparedStatement ps = conn.prepareStatement(sql);
                 ps.executeUpdate(sql);
            } while (want.equals("y"));
        }
        catch(SQLException se) {
            System.out.println(se);
        }
    }
    public void CreateUserRecord(String sid) {
        try {
            String want;
            do {
                Scanner sc3 = new Scanner(System.in);
                System.out.println("Enter your User name  :");
                String name = sc3.next();
                System.out.println("Enter your ID");
                int uid = sc3.nextInt();

                System.out.println("want you add more record :");
                want = sc3.next();

                String sql="INSERT INTO USER(ID,NAME,OID)"+"VALUES('"+uid+"','"+name+"','"+sid+"');";

                stmt = conn.prepareStatement(sql);
                stmt.execute(sql);
            } while (want.equals("y"));
        } catch(SQLException se) {
            System.out.println(se);
        }
    }
    public void UpdateOrganisation() {
        try {
            Scanner Upsc = new Scanner(System.in);
            System.out.println("Enter your Organisation Id  :");
            int sid = Upsc.nextInt();
            System.out.println("Update your Organisation name :");
            String  O_name = Upsc.next();

            String sql = "update ORGANISATION set O_name = '" +O_name +"' where sid = '" +sid+ "'";
            stmt = conn.prepareStatement(sql);
            stmt.executeUpdate(sql);
            System.out.println("Database updated successfully ");
        }
        catch (SQLException se)  {
            System.out.println(se);
        }
    }

    public void UpdateUser() {
        try {
            Scanner Upsc = new Scanner(System.in);
            System.out.println("Enter your User ID   :");
            int uid = Upsc.nextInt();
            System.out.println("Update your name  :");
            String name = Upsc.next();
            String sql = "update USER set Name = '" +name +"' where ID = '" +uid+ "'";
            stmt = conn.prepareStatement(sql);
            stmt.executeUpdate(sql);
            System.out.println("Database updated successfully ");
        }
        catch(SQLException se) {
            System.out.println(se);
        }
    }                           


    public void RemoveOrganisation(){
        try {
            Scanner rmsc = new Scanner(System.in);
            System.out.println("Eneter the Organisation UD  :");
            int sid = rmsc.nextInt();
            String sql = "delete from ORGANISATION where sid='" +sid+ "'";
            String sql1 = "delete from USER where OID='" +sid+ "'";
            stmt = conn.prepareStatement(sql1);
            stmt.executeUpdate(sql1);
            stmt = conn.prepareStatement(sql);
            stmt.executeUpdate(sql);
            System.out.println("Record Organisation successfully");
            } catch (SQLException se) {
            System.out.println(se);
        }
    }
    public void RemoveUser(){
        try {
            Scanner rmsc = new Scanner(System.in);
            System.out.println("Eneter the User ID  :");
            int uid = rmsc.nextInt();
            String sql = "delete from USER where ID ='" +uid+ "'";
            stmt = conn.prepareStatement(sql);
            stmt.executeUpdate(sql);
            System.out.println("Record deleted successfully");
        }
        catch (SQLException se) {
            System.out.println(se);
        }
    }
    public  void PrintOrganisation(){


        try {

            String sql = "select * from ORGANISATION ";
            stmt = conn.prepareStatement(sql);
            ResultSet rs = stmt.executeQuery(sql);
            ResultSetMetaData rsmd = rs.getMetaData();
            System.out.println("Details of Organisation ");
            int columnsNumber = rsmd.getColumnCount();
            while (rs.next()) {
                for (int i = 1; i <= columnsNumber; i++) {
                    if (i > 1) System.out.print(",  ");
                    String columnValue = rs.getString(i);
                    System.out.print(columnValue + " " + rsmd.getColumnName(i));
                }
                System.out.println("");
            }
           
        }

        catch (SQLException se) {
            System.out.println(se);
        }
    }

    public  void PrintUser(){
        try {

            String sql = "select * from USER ";
            stmt = conn.prepareStatement(sql);
            ResultSet rs = stmt.executeQuery(sql);
            ResultSetMetaData rsmd = rs.getMetaData();
            System.out.println("Details of User ");
            int columnsNumber = rsmd.getColumnCount();
            while (rs.next()) {
                for (int i = 1; i <= columnsNumber; i++) {
                    if (i > 1) System.out.print(",  ");
                    String columnValue = rs.getString(i);
                    System.out.print(columnValue + " " + rsmd.getColumnName(i));
                }
                System.out.println("");
            }

        }
        catch (SQLException se) {
            System.out.println(se);
        }
    }
    public static void UserMenu() {
        try {
        int Input2;
        Scanner sc2 = new Scanner(System.in);
            Project c = new Project();
            do {
        System.out.println("1. Create User :");
        System.out.println("2. Update User :");
        System.out.println("3. Remove User :");
        System.out.println("4. Press 0 go back to Main menu");
        System.out.println("Enter your choice :");
        Input2=sc2.nextInt();
                switch (Input2) {
                    case 1:
                        c.LoginDtabase();
                        break;
                    case 2:
                        c.UpdateUser();
                        break;
                    case 3:
                        c.RemoveUser();
                        break;
                    default:
                        System.out.println("Wrong Input");
                }

            }
            while(Input2 != 0);
        }

        catch (Exception e)
        {
            System.out.println(e);
        }

    }

    public static void main(String... s) {
        String DB_URL = "jdbc:mysql://localhost:3306/SuperAdmin";
        String USER = "root";
        String PASS = "toor";

        try {


            Class.forName("com.mysql.jdbc.Driver");

            System.out.println("Connecting to database...");
            conn = DriverManager.getConnection(DB_URL, USER, PASS);
            System.out.println("Connected to database...");


            Project c = new Project();
            c.CreateDatabase();
            int Input;
            do {
                Input = Menu();
                switch (Input) {
                    case 1:
                        c.OrganisationMenu();
                        break;
                    case 2:
                        c.UserMenu();
                        break;
                    case 3:
                        c.PrintOrganisation();
                        break;
                    case 4:
                        c.PrintUser();
                        break;
                    case 5:
                        System.exit(1);
                    default:
                        System.out.println("Wrong Input");

                }

            }
            while(Input != 0);
            conn.close();
            System.out.println("Now Connection is closed");
        }

        catch (Exception e)
        {
            System.out.println(e);
        }
    }
}
