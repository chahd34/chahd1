
//
// Source code recreated from a .class file by IntelliJ IDEA
// (powered by FernFlower decompiler)
//

import java.time.LocalDate;
import java.util.ArrayList;
import java.util.Iterator;
import java.util.List;
import java.util.Scanner;

public class memberadd {
    private static List<ClubMember> members = new ArrayList();
    private static List<ClubDepartment> departments = new ArrayList();
    private static Scanner scanner;

    public memberadd() {
    }

    public static void main(String[] args) {
        while(true) {
            System.out.println("Which operation do you want to use? (add-member / view-member / update-member / delete-member)");
            String operation = scanner.nextLine();
            switch (operation.toLowerCase()) {
                case "add-member":
                    addMember();
                    break;
                case "view-member":
                    viewMember();
                    break;
                case "update-member":
                    updateMember();
                    break;
                case "delete-member":
                    deleteMember();
                    break;
                default:
                    System.out.println("Invalid operation. Please try again.");
            }
        }
    }

    private static void addMember() {
        System.out.println("Enter member details:");
        System.out.print("ID: ");
        int id = Integer.parseInt(scanner.nextLine());
        System.out.print("Name: ");
        String name = scanner.nextLine();
        System.out.print("Middle Name: ");
        String midlName = scanner.nextLine();
        System.out.print("First Name: ");
        String firstName = scanner.nextLine();
        System.out.print("Birth Date (YYYY-MM-DD): ");
        LocalDate birthDate = LocalDate.parse(scanner.nextLine());
        System.out.print("Birth Location: ");
        String birthLocation = scanner.nextLine();
        System.out.print("University: ");
        String university = scanner.nextLine();
        System.out.print("Speciality: ");
        String speciality = scanner.nextLine();
        System.out.print("Study Level: ");
        String studyLevel = scanner.nextLine();
        System.out.print("Bio: ");
        String bio = scanner.nextLine();
        System.out.print("Profile Image (fe2f09d9b9a25d255e393328fb40969f.jpg): ");
        String profileImage = scanner.nextLine();
        System.out.print("Department Name: ");
        String deptName = scanner.nextLine();
        ClubDepartment department = new ClubDepartment(departments.size() + 1, deptName, "Default Description");
        departments.add(department);
        ClubMember member = new ClubMember(id, name, midlName, firstName, birthDate, birthLocation, department, university, speciality, studyLevel, bio, profileImage);
        members.add(member);
        System.out.println("Member added successfully!");
    }

    private static void viewMember() {
        System.out.print("Enter Member ID to view: ");
        int id = Integer.parseInt(scanner.nextLine());
        Iterator var1 = members.iterator();

        ClubMember member;
        do {
            if (!var1.hasNext()) {
                System.out.println("Member not found!");
                return;
            }

            member = (ClubMember)var1.next();
        } while(member.idPerson != id);

        System.out.println("Member Details:");
        System.out.println("Name: " + member.name + " " + member.midlName + " " + member.firstName);
        System.out.println("Birth Date: " + String.valueOf(member.birthDate));
        System.out.println("University: " + member.university);
        System.out.println("Speciality: " + member.speciality);
    }

    private static void updateMember() {
        System.out.print("Enter Member ID to update: ");
        int id = Integer.parseInt(scanner.nextLine());
        Iterator var1 = members.iterator();

        ClubMember member;
        do {
            if (!var1.hasNext()) {
                System.out.println("Member not found!");
                return;
            }

            member = (ClubMember)var1.next();
        } while(member.idPerson != id);

        System.out.println("Enter new details (leave blank to keep current value):");
        System.out.print("Name (" + member.name + "): ");
        String name = scanner.nextLine();
        if (!name.isBlank()) {
            member.name = name;
        }

        System.out.print("University (" + member.university + "): ");
        String university = scanner.nextLine();
        if (!university.isBlank()) {
            member.university = university;
        }

        System.out.print("Speciality (" + member.speciality + "): ");
        String speciality = scanner.nextLine();
        if (!speciality.isBlank()) {
            member.speciality = speciality;
        }

        System.out.println("Member updated successfully!");
    }

    private static void deleteMember() {
        System.out.print("Enter Member ID to delete: ");
        int id = Integer.parseInt(scanner.nextLine());
        members.removeIf((member) -> {
            return member.idPerson == id;
        });
        System.out.println("Member deleted successfully!");
    }

    static {
        scanner = new Scanner(System.in);
    }
}

