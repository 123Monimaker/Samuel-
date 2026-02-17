#include <iostream>
#include <fstream>
#include <string>
using namespace std;

class Student {
    string id, name;
    bool present;
public:
    void setData(string i, string n) { id=i; name=n; present=false; }
    void markPresent() { present=true; }
    void display() { cout << id << " " << name << " " << (present?"Present":"Absent") << endl; }
    string getId() { return id; }
    bool isPresent() { return present; }
};

const string FILE_NAME = "attendance.txt";

void addStudent() {
    string id, name;
    cout << "Enter ID: "; cin >> id;
    cout << "Enter Name: "; cin.ignore(); getline(cin, name);
    Student s; s.setData(id, name);
    ofstream file(FILE_NAME, ios::app);
    file << id << "," << name << ",Absent\n";
    file.close();
    cout << "Student added.\n";
}

void markAttendance() {
    string id;
    cout << "Enter ID to mark present: "; cin >> id;
    ifstream file(FILE_NAME);
    ofstream temp("temp.txt");
    string line;
    bool found = false;
    while(getline(file, line)) {
        if(line.find(id) != string::npos) {
            temp << line.substr(0, line.rfind(",")) << ",Present\n";
            found = true;
        } else {
            temp << line << endl;
        }
    }
    file.close(); temp.close();
    remove(FILE_NAME.c_str()); rename("temp.txt", FILE_NAME.c_str());
    if(found) cout << "Attendance marked.\n";
    else cout << "ID not found.\n";
}

void viewAttendance() {
    ifstream file(FILE_NAME);
    string line;
    while(getline(file, line)) {
        cout << line << endl;
    }
    file.close();
}

int main() {
    int choice;
    do {
        cout << "1. Add Student\n2. Mark Attendance\n3. View Attendance\n4. Exit\n";
        cin >> choice;
        switch(choice) {
            case 1: addStudent(); break;
            case 2: markAttendance(); break;
            case 3: viewAttendance(); break;
        }
    } while(choice != 4);
    return 0;
}