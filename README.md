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
    #include <iostream>
#include <vector>
#include <iomanip>
using namespace std;

int main() {
    int n;
    cout << "Enter number of courses: ";
    cin >> n;

    vector<string> grades(n);
    vector<int> credits(n);
    vector<double> gradePoints(n);

    double totalGradePoints = 0;
    int totalCredits = 0;

    for (int i = 0; i < n; i++) {
        cout << "\nCourse " << i + 1 << endl;

        cout << "Enter Grade (A, B, C, D, F): ";
        cin >> grades[i];

        cout << "Enter Credit Hours: ";
        cin >> credits[i];

        if (grades[i] == "A")
            gradePoints[i] = 4.0;
        else if (grades[i] == "B")
            gradePoints[i] = 3.0;
        else if (grades[i] == "C")
            gradePoints[i] = 2.0;
        else if (grades[i] == "D")
            gradePoints[i] = 1.0;
        else
            gradePoints[i] = 0.0;

        totalGradePoints += gradePoints[i] * credits[i];
        totalCredits += credits[i];
    }

    double cgpa = totalGradePoints / totalCredits;

    cout << "\n===== RESULT =====\n";
    for (int i = 0; i < n; i++) {
        cout << "Course " << i + 1
             << " Grade: " << grades[i]
             << " Credit Hours: " << credits[i] << endl;
    }

    cout << fixed << setprecision(2);
    cout << "\nCGPA = " << cgpa << endl;

    return 0;
}
print("Simple Chatbot")
print("Type 'bye' to exit")

while True:
    user = input("You: ").lower()

    if user == "hello":
        print("Bot: Hi!")
    elif user == "how are you":
        print("Bot: I am fine, thanks!")
    elif user == "what is your name":
        print("Bot: My name is ChatBot.")
    elif user == "bye":
        print("Bot: Goodbye!")
        break
    else:
        print("Bot: Sorry, I don't understand.")
        import random

words = ["apple", "mango", "grapes", "banana", "orange"]
word = random.choice(words)

guessed = []
tries = 6

print("Welcome to Hangman!")

while tries > 0:
    display = ""

    for letter in word:
        if letter in guessed:
            display += letter + " "
        else:
            display += "_ "

    print(display)

    if "_" not in display:
        print("Congratulations! You guessed the word:", word)
        break

    guess = input("Guess a letter: ").lower()

    if guess in word:
        guessed.append(guess)
        print("Correct!")
    else:
        tries -= 1
        print("Wrong! Tries left:", tries)

if tries == 0:
    print("Game Over! The word was:", word)
    stocks = {
    "AAPL": 180,
    "TSLA": 250,
    "GOOG": 140,
    "AMZN": 150
}

total = 0

print("Stock Portfolio Tracker")

for stock, price in stocks.items():
    qty = int(input(f"Enter quantity of {stock}: "))
    total += qty * price

print("Total Investment Value: $", total)

save = input("Save result to file? (yes/no): ")

if save.lower() == "yes":
    file = open("portfolio.txt", "w")
    file.write("Total Investment Value: $" + str(total))
    file.close()
    print("Saved in portfolio.txt")
    return 0;
}
