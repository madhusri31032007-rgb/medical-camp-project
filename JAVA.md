import java.util.ArrayList;
import java.util.Scanner;

class Patient {
    int id;
    String name;
    int age;
    String gender;
    String disease;
    String phone;

    Patient(int id, String name, int age, String gender, String disease, String phone) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.gender = gender;
        this.disease = disease;
        this.phone = phone;
    }

    public void display() {
        System.out.println("-----------------------------------------");
        System.out.println("Patient ID : " + id);
        System.out.println("Name       : " + name);
        System.out.println("Age        : " + age);
        System.out.println("Gender     : " + gender);
        System.out.println("Disease    : " + disease);
        System.out.println("Phone      : " + phone);
    }
}

public class MedicalCampRegistration {

    static ArrayList<Patient> patients = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {

        int choice;

        do {
            System.out.println("\n===== MEDICAL CAMP REGISTRATION SYSTEM =====");
            System.out.println("1. Register Patient");
            System.out.println("2. View All Patients");
            System.out.println("3. Search Patient");
            System.out.println("4. Update Patient");
            System.out.println("5. Delete Patient");
            System.out.println("6. Exit");
            System.out.print("Enter your choice: ");

            choice = sc.nextInt();

            switch (choice) {
                case 1:
                    registerPatient();
                    break;

                case 2:
                    viewPatients();
                    break;

                case 3:
                    searchPatient();
                    break;

                case 4:
                    updatePatient();
                    break;

                case 5:
                    deletePatient();
                    break;

                case 6:
                    System.out.println("Thank You!");
                    break;

                default:
                    System.out.println("Invalid Choice!");
            }

        } while (choice != 6);
    }

    static void registerPatient() {

        System.out.print("Enter Patient ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Name: ");
        String name = sc.nextLine();

        System.out.print("Enter Age: ");
        int age = sc.nextInt();
        sc.nextLine();

        System.out.print("Enter Gender: ");
        String gender = sc.nextLine();

        System.out.print("Enter Disease: ");
        String disease = sc.nextLine();

        System.out.print("Enter Phone Number: ");
        String phone = sc.nextLine();

        patients.add(new Patient(id, name, age, gender, disease, phone));

        System.out.println("Patient Registered Successfully!");
    }

    static void viewPatients() {

        if (patients.isEmpty()) {
            System.out.println("No Patient Records Found.");
            return;
        }

        for (Patient p : patients) {
            p.display();
        }
    }

    static void searchPatient() {

        System.out.print("Enter Patient ID: ");
        int id = sc.nextInt();

        for (Patient p : patients) {
            if (p.id == id) {
                p.display();
                return;
            }
        }

        System.out.println("Patient Not Found.");
    }

    static void updatePatient() {

        System.out.print("Enter Patient ID: ");
        int id = sc.nextInt();
        sc.nextLine();

        for (Patient p : patients) {

            if (p.id == id) {

                System.out.print("Enter New Name: ");
                p.name = sc.nextLine();

                System.out.print("Enter New Age: ");
                p.age = sc.nextInt();
                sc.nextLine();

                System.out.print("Enter New Gender: ");
                p.gender = sc.nextLine();

                System.out.print("Enter New Disease: ");
                p.disease = sc.nextLine();

                System.out.print("Enter New Phone: ");
                p.phone = sc.nextLine();

                System.out.println("Patient Updated Successfully!");
                return;
            }
        }

        System.out.println("Patient Not Found.");
    }

    static void deletePatient() {

        System.out.print("Enter Patient ID: ");
        int id = sc.nextInt();

        for (Patient p : patients) {

            if (p.id == id) {
                patients.remove(p);
                System.out.println("Patient Deleted Successfully!");
                return;
            }
        }

        System.out.println("Patient Not Found.");
    }
}