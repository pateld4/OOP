# OOP
import java.util.Scanner;

public class LastName {

	Scanner sc = new Scanner(System.in);
        
        public String checkYear() {
            String academicYear = "";
           
            System.out.println("Enter Academic Year: ");
            academicYear = sc.nextLine();

            if ("Senior".equals(academicYear) || "Junior".equals(academicYear) || "Sophomore".equals(academicYear) || "Freshman".equals(academicYear)) {
                return academicYear;
            } else {
                System.out.println("Please enter a valid Academic Year (Senior, Junior, Sophomore, Freshmam)");
                academicYear = checkYear();
            }
            
            
            return academicYear;
        }

	public double checkGPA() {
            
                //Set variable for GPA
		double Students_GPA = 0;
		
                //Creating menu option for GPA
                try{
			System.out.println("Enter the Students GPA: ");
			Students_GPA = Double.parseDouble(sc.nextLine());
                        
                        //Set filter for GPA
                        if(Students_GPA >= 0.0 && Students_GPA <= 4.0)
			{
				return Students_GPA;
			}
			else{
				System.out.println("Please enter Students GPA value between 0.0 to 4.0.");
				Students_GPA = checkGPA();
			}
		}
		catch (Exception e) {
			System.out.println("Please Enter Only Float value.");
			Students_GPA = checkGPA();
		}
		return Students_GPA;
	}
	
	public void PrintMenu(Student m) {
		try {
			System.out.println("1. Enter the Students Name");
			System.out.println("2. Enter the Students Academic Year");
			System.out.println("3. Enter the Students GPA");
			System.out.println("4. Display Students Info");
			System.out.println("5. Exit");

			System.out.print("Please enter which number you want to answer: ");

			byte choice = Byte.parseByte(sc.nextLine());
                        
                        //Creating a menu option cases
			switch (choice) {
			case 1:
				System.out.println("Enter Students Name: ");
				String Students_Name = sc.nextLine();
				m.setStudents_Name(Students_Name);
				break;
			case 2:
				String Students_Year = checkYear();
				m.setStudents_Year(Students_Year);
				break;
			case 3:
				double Students_GPA = checkGPA();
				m.setStudents_GPA(Students_GPA);
				break;
			case 4:
				if (m.getStudents_Name() == null || m.getStudents_Year() == null || m.getStudents_GPA() == 0) {
					System.out.println("Please answer all questions");
				} else {
					System.out.println("The students name is: " + m.getStudents_Name());
					System.out.println("The students academic year is: " + m.getStudents_Year());
					System.out.println("The students GPA is: " + m.getStudents_GPA());
					boolean flag = true;
					while (flag) {
						System.out.println("Type clear to clear the terminal screen to continue");
						System.out.println("1. Yes");
						System.out.println("2. No");
						byte subchoice = Byte.parseByte(sc.nextLine());
						switch (subchoice) {
						case 1:
							m = new Student();
							flag = false;
							break;
						case 2:
							System.out.println("you continue for show data.");
							flag = false;
							break;
						default:
							System.out.println("Please enter 1 or 2.");
							break;
						}
					}
				}
				break;
                        case 5:
				System.exit(0);;
				break;
			default:
				System.out.println("Please enter choice between 1 to 7, Thanks.");
				break;
			}

		} catch (Exception e) {
			System.out.println("Please Enter Proper Data.Thanks.");
		}
		PrintMenu(m);
	}

	public static void main(String[] args) {
		LastName l = new LastName();
		l.PrintMenu(new Student());
	}

}
