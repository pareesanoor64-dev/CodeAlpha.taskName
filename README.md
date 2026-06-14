# CodeAlpha.taskName
include <iostream>
#include <fstream>
#include <string>
using namespace std;

void registerUser() {
    string username, password;

    cout << "Enter Username: ";
    cin >> username;

    cout << "Enter Password: ";
    cin >> password;

    ofstream file(username + ".txt");
    file << username << endl;
    file << password << endl;
    file.close();

    cout << "Registration Successful!\n";
}

void loginUser() {
    string username, password;
    string storedUser, storedPass;

    cout << "Enter Username: ";
    cin >> username;

    cout << "Enter Password: ";
    cin >> password;

    ifstream file(username + ".txt");

    if (!file) {
        cout << "User not found!\n";
        return;
    }

    getline(file, storedUser);
    getline(file, storedPass);

    if (username == storedUser && password == storedPass)
        cout << "Login Successful!\n";
    else
        cout << "Invalid Password!\n";

    file.close();
}

int main() {
    int choice;

    do {
        cout << "\n1. Register";
        cout << "\n2. Login";
        cout << "\n3. Exit";
        cout << "\nEnter Choice: ";
        cin >> choice;

        switch(choice) {
            case 1:
                registerUser();
                break;
            case 2:
                loginUser();
                break;
            case 3:
                cout << "Goodbye!\n";
                break;
            default:
                cout << "Invalid Choice!\n";
        }

    } while(choice != 3);

    return 0;
}
