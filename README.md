#include <iostream>
#include <fstream>
#include <string>

using namespace std;

class BOOK {
public:
    void list();
    string booktitle(int);

protected:
    void add_new_book(int, string, string, float, int, string);
    void update_books(int, int, int);
    int available(int);
    void delete_record(int);

private:
    int ISBN, books;
    string title, author;
};

class operate_books : public BOOK {
public:
    void add_new_book() {
        int ISBN, year;
        string title, author, status;
        float price;

        // Adding books to catalogue
        cout << "ADD BOOKS TO CATALOGUE\n\n";

        cout << "ISBN: ";
        cin >> ISBN;
        cin.ignore();  // Ignore newline character left by `cin`

        cout << "Title of the book: ";
        getline(cin, title);

        cout << "Author of the Book: ";
        getline(cin, author);

        cout << "Price: ";
        cin >> price;

        cout << "Year of Publication: ";
        cin >> year;
        cin.ignore();  // Ignore newline after int input

        cout << "Status of the Book (Available/Not Available): ";
        getline(cin, status);

        cout << "\nBook added successfully!\n";

        // Saving to file
        add_to_catalogue(ISBN, title, author, price, year, status);
    }

    int add_to_catalogue(int ISBN, string title, string author, float price, int year, string status) {
        ofstream file("data.txt", ios::app);  // Open file in append mode

        if (!file) {
            cout << "Error opening file!\n";
            return 0;
        }

        file << ISBN << ", " << title << ", " << author << ", " << price << ", " << year << ", " << status << endl;
        file.close();

       return 0;
    }

    void view_books() {
        ifstream file("data.txt");
        string line;
        if (!file) {
            cout << "Error: Could not open file!" << endl;
            return;
        }
        while (getline(file, line)) {
            cout << line << endl;
        }
        file.close();
    }
void update_books(int, int, int){
    int add_to_catalogue(int ISBN, string title, string author, float price, int year, string status);
    cout << "Book catalogue updated successfully!\n";
}
void delete_record(){
string line, title;
cout<<"Please enter the title or ISBN of the book you want to delete"<<endl;
cin>>title;
ifstream file;
file.open("data.txt");
while (getline(file, line)){
    if (line !=title)
    cout<<line<<endl;
}
cout<<"The book with the name "<<title<<" has been if it existed"<<endl;
file.close();
remove("data.txt");
}
};

int main() {
    operate_books obj;

    obj.add_new_book();  // Call the function without passing uninitialized variables
    obj.view_books(); //call the fuction view books
    obj.delete_record(); //call the delete record function 

    return 0;
}


