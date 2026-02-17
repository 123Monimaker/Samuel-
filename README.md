#include <iostream>
using namespace std;

void add() { cout << "Adding...\n"; }
void view() { cout << "Viewing...\n"; }

int main() {
    int choice;
    do {
        cout << "1. Add\n2. View\n3. Exit\n";
        cin >> choice;
        switch(choice) {
            case 1: add(); break;
            case 2: view(); break;
        }
    } while(choice != 3);
    return 0;
}