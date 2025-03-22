# Student-grading-system
#include <iostream>
#include <string>

using namespace std;

class Student {
private:
    string name;
    int rollNo;
    float marks[5]; // Assuming 5 subjects
    float totalMarks = 0;
    float percentage = 0;
    char grade;

public:
    void inputDetails() {
        cout << "Enter Student Name: ";
        cin.ignore(); // To ignore any leftover newline characters
        getline(cin, name);
        
        cout << "Enter Roll Number: ";
        cin >> rollNo;

        cout << "Enter marks for 5 subjects: " << endl;
        for (int i = 0; i < 5; i++) {
            cout << "Subject " << i + 1 << ": ";
            cin >> marks[i];
            totalMarks += marks[i];
        }

        calculateGrade();
    }

    void calculateGrade() {
        percentage = totalMarks / 5; // Assuming each subject is out of 100

        if (percentage >= 90)
            grade = 'A';
        else if (percentage >= 80)
            grade = 'B';
        else if (percentage >= 70)
            grade = 'C';
        else if (percentage >= 60)
            grade = 'D';
        else
            grade = 'F';
    }

    void displayResult() {
        cout << "\n----------------------" << endl;
        cout << "Student Name: " << name << endl;
        cout << "Roll Number: " << rollNo << endl;
        cout << "Total Marks: " << totalMarks << " / 500" << endl;
        cout << "Percentage: " << percentage << "%" << endl;
        cout << "Grade: " << grade << endl;
        cout << "----------------------\n";
    }
};

int main() {
    Student student;

    student.inputDetails();
    student.displayResult();

    return 0;
}
