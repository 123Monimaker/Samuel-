#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main() {
    srand(time(0));
    int secretNumber = rand() % 100 + 1;
    int guess = 0;
    bool gameWon = false;

    cout << "Welcome to the Number Guessing Game!" << endl;
    cout << "I'm thinking of a number between 1 and 100." << endl;

    while (!gameWon) {
        cout << "Enter your guess: ";
        cin >> guess;

        if (guess == secretNumber) {
            cout << "Congratulations! You guessed the secret Number!" << endl;
            gameWon = true;
        } else if (guess < secretNumber) {
            cout << "Too Low! Try again." << endl;
        } else {
            cout << "Too High! Try again." << endl;
        }
    }

    return 0;
}