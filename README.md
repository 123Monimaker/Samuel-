#include <fstream>
#include <iostream>
using namespace std;

int main() {
    ofstream file("data.txt");
    file << "Hello, Ghana!";
    file.close();

    ifstream read("data.txt");
    string line;
    getline(read, line);
    cout << line;
    read.close();
    return 0;
}