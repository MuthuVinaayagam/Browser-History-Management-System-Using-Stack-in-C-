# Browser-History-Management-System-Using-Stack-in-C-
A Browser History Management System implemented in C++ using a stack data structure. It allows users to visit web pages, navigate back to previously visited pages, and display browsing history. Demonstrates stack operations, push, pop, and Last In, First Out (LIFO) principles.

#include <iostream>
#include <string>
using namespace std;

class Stack {
    string page[10];
    int top;

public:
    Stack() {
        top = -1;
    }

    void push(string value);
    string pop();
    void display();
};

void Stack::push(string value) {
    if (top == 9) {
        cout << "Browser history is full.\n";
        return;
    }

    page[++top] = value;
    cout << "Page visited successfully.\n";
}

string Stack::pop() {
    if (top == -1) {
        cout << "No history to go back to.\n";
        return "";
    }

    return page[top--];
}

void Stack::display() {
    if (top == -1) {
        cout << "No browser history.\n";
        return;
    }

    cout << "Browser history:";
    for (int i = top; i >= 0; i--) {
        cout << "\n" << page[i];
    }
    cout << '\n';
}

int main() {
    Stack s;
    int ch;
    string page1, page2;

    do {
        cout << "\n1. Visit page";
        cout << "\n2. Back";
        cout << "\n3. Display history";
        cout << "\n4. Exit";
        cout << "\nEnter your choice: ";

        if (!(cin >> ch)) {
            cout << "Invalid input.\n";
            cin.clear();
            cin.ignore(10000, '\n');
            continue;
        }

        switch (ch) {
        case 1:
            cout << "Enter the page: ";
            cin >> page1;
            s.push(page1);
            break;

        case 2:
            page2 = s.pop();
            if (!page2.empty()) {
                cout << "Back from page: " << page2 << '\n';
            }
            break;

        case 3:
            s.display();
            break;

        case 4:
            cout << "Exiting browser history.\n";
            break;

        default:
            cout << "Invalid choice. Select 1 to 4.\n";
        }

    } while (ch != 4);

    return 0;
}
