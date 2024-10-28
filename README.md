class Student:
    def __init__(self, roll_no, name, age, grade):
        self.roll_no = roll_no
        self.name = name
        self.age = age
        self.grade = grade

class SchoolManagementSystem:
    def __init__(self):
        self.students = []

    def add_student(self, roll_no, name, age, grade):
        student = Student(roll_no, name, age, grade)
        self.students.append(student)
        print(f"Student {name} added successfully!")

    def delete_student(self, roll_no):
        for i, student in enumerate(self.students):
            if student.roll_no == roll_no:
                del self.students[i]
                print(f"Student with roll number {roll_no} deleted successfully!")
                return
        print(f"Student with roll number {roll_no} not found!")

    def display_students(self):
        if not self.students:
            print("No students in the system.")
            return
        print("List of students:")
        for student in self.students:
            print(f"Roll No: {student.roll_no}, Name: {student.name}, Age: {student.age}, Grade: {student.grade}")

    def update_student(self, roll_no, name=None, age=None, grade=None):
        for student in self.students:
            if student.roll_no == roll_no:
                if name:
                    student.name = name
                if age:
                    student.age = age
                if grade:
                    student.grade = grade
                print(f"Student with roll number {roll_no} updated successfully!")
                return
        print(f"Student with roll number {roll_no} not found!")

def main():
    sms = SchoolManagementSystem()
    
    while True:
        print("\nSchool Management System")
        print("1. Add Student")
        print("2. Delete Student")
        print("3. Display Students")
        print("4. Update Student")
        print("5. Exit")

        choice = input("Enter your choice: ")

        if choice == '1':
            roll_no = input("Enter roll number: ")
            name = input("Enter name: ")
            age = int(input("Enter age: "))
            grade = input("Enter grade: ")
            sms.add_student(roll_no, name, age, grade)
        elif choice == '2':
            roll_no = input("Enter roll number to delete: ")
            sms.delete_student(roll_no)
        elif choice == '3':
            sms.display_students()
        elif choice == '4':
            roll_no = input("Enter roll number to update: ")
            name = input("Enter new name (press Enter to skip): ")
            age = input("Enter new age (press Enter to skip): ")
            grade = input("Enter new grade (press Enter to skip): ")
            sms.update_student(roll_no, name, age, grade)
        elif choice == '5':
            print("Exiting...")
            break
        else:
            print("Invalid choice. Please try again.")

if __name__ == "__main__":
    main()# School-management-system
