# Given string
Str = "Fundamentals of Data Structure of Data Science"

# a) Function to display the word with the longest length
def longest_word():
    words = Str.split()
    longest = max(words, key=len)
    print(f"The longest word is: '{longest}' with length {len(longest)}")

# b) Function to determine the frequency of occurrence of a particular character
def char_frequency():
    char = input("Enter a character to find its frequency: ")
    count = Str.count(char)
    print(f"The character '{char}' appears {count} times in the string.")

# c) Function to check whether the given string is palindrome or not
def is_palindrome():
    input_str = input("Enter a string to check if it's a palindrome: ")
    if input_str == input_str[::-1]:
        print("The string is a palindrome.")
    else:
        print("The string is not a palindrome.")

# d) Function to display the index of first appearance of the substring
def substring_index():
    substring = input("Enter a substring to find its first appearance index: ")
    index = Str.find(substring)
    if index != -1:
        print(f"The first occurrence of the substring '{substring}' is at index {index}.")
    else:
        print(f"The substring '{substring}' is not found in the string.")

# e) Function to count the occurrences of each word in the string
def word_frequency():
    words = Str.split()
    word_count = {}
    for word in words:
        word_count[word] = word_count.get(word, 0) + 1

    print("Occurrences of each word in the string:")
    for word, count in word_count.items():
        print(f"'{word}': {count}")

# Main program
if __name__ == '__main__':
    while True:
        print("\nChoose an operation:")
        print("1. Display the word with the longest length")
        print("2. Determine the frequency of a particular character")
        print("3. Check whether the given string is a palindrome")
        print("4. Display the index of the first appearance of a substring")
        print("5. Count the occurrences of each word in the string")
        print("6. Exit")

        choice = int(input("Enter your choice: "))

        if choice == 1:
            longest_word()
        elif choice == 2:
            char_frequency()
        elif choice == 3:
            is_palindrome()
        elif choice == 4:
            substring_index()
        elif choice == 5:
            word_frequency()
        elif choice == 6:
            print("Exiting the program.")
            break
        else:
            print("Invalid choice, please try again.")


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
dsl practical 1


# Function to find students who play both cricket and badminton
def students_play_both(cricket_players, badminton_players):
   students = [ for student in cricket_players if student in badminton_players]
   return students

# Function to find students who play either cricket or badminton but not both
def students_play_either_not_both(cricket_players, badminton_players):
    return [student for student in cricket_players if student not in badminton_players] + \
           [student for student in badminton_players if student not in cricket_players]

# Function to count students who play neither cricket nor badminton
def students_play_neither(cricket_players, badminton_players, all_students):
    return len([student for student in all_students if student not in cricket_players and student not in badminton_players])

# Function to count students who play cricket and football but not badminton
def students_play_cricket_football_not_badminton(cricket_players, football_players, badminton_players):
    return len([student for student in cricket_players if student in football_players and student not in badminton_players])

# Example data
cricket_players = ['John', 'Alice', 'Bob', 'David', 'Emma']
badminton_players = ['Alice', 'Emma', 'George', 'Hannah']
football_players = ['Bob', 'David', 'John', 'George']

# All students
all_students = ['John', 'Alice', 'Bob', 'David', 'Emma', 'George', 'Hannah']

# a) List of students who play both cricket and badminton
both_players = students_play_both(cricket_players, badminton_players)
print("Students who play both cricket and badminton:", both_players)

# b) List of students who play either cricket or badminton but not both
either_not_both = students_play_either_not_both(cricket_players, badminton_players)
print("Students who play either cricket or badminton but not both:", either_not_both)

# c) Number of students who play neither cricket nor badminton
neither_count = students_play_neither(cricket_players, badminton_players, all_students)
print("Number of students who play neither cricket nor badminton:", neither_count)

# d) Number of students who play cricket and football but not badminton
cricket_football_not_badminton = students_play_cricket_football_not_badminton(cricket_players, football_players, badminton_players)
print("Number of students who play cricket and football but not badminton:", cricket_football_not_badminton)

--------------------------------------------------------------------------------------------------------------------------------------------------------
dsl practical 3


# Function to print a matrix
def print_matrix(matrix):
    for row in matrix:
        print(row)

# Input matrices from the user
print("Enter Matrix A:")
rows_A = int(input("Enter number of rows: "))
cols_A = int(input("Enter number of columns: "))
A = []
print("Enter the elements row-wise:")
for i in range(rows_A):
    row = []
    for j in range(cols_A):
        row.append(int(input(f"Enter element A[{i}][{j}]: ")))
    A.append(row)

print("\nEnter Matrix B:")
rows_B = int(input("Enter number of rows: "))
cols_B = int(input("Enter number of columns: "))
B = []
print("Enter the elements row-wise:")
for i in range(rows_B):
    row = []
    for j in range(cols_B):
        row.append(int(input(f"Enter element B[{i}][{j}]: ")))
    B.append(row)

# Display menu and perform selected operation
while True:
    print("\nMatrix Operations Menu:")
    print("1. Addition")
    print("2. Subtraction")
    print("3. Multiplication")
    print("4. Transpose of Matrix A")
    print("5. Transpose of Matrix B")
    print("6. Exit")

    choice = input("Enter your choice (1-6): ")

    if choice == '1':
        # Addition of matrices
        if rows_A == rows_B and cols_A == cols_B:
            result = [[0] * cols_A for _ in range(rows_A)]
            for i in range(rows_A):
                for j in range(cols_A):
                    result[i][j] = A[i][j] + B[i][j]
            print("\nResult of Addition:")
            print_matrix(result)
        else:
            print("Matrix dimensions must match for addition")

    elif choice == '2':
        # Subtraction of matrices
        if rows_A == rows_B and cols_A == cols_B:
            result = [[0] * cols_A for _ in range(rows_A)]
            for i in range(rows_A):
                for j in range(cols_A):
                    result[i][j] = A[i][j] - B[i][j]
            print("\nResult of Subtraction:")
            print_matrix(result)
        else:
            print("Matrix dimensions must match for subtraction")

    elif choice == '3':
        # Multiplication of matrices
        if cols_A == rows_B:
            result = [[0] * cols_B for _ in range(rows_A)]
            for i in range(rows_A):
                for j in range(cols_B):
                    for k in range(cols_A):
                        result[i][j] += A[i][k] * B[k][j]
            print("\nResult of Multiplication:")
            print_matrix(result)
        else:
            print("Number of columns in first matrix must be equal to number of rows in second matrix for multiplication")

    elif choice == '4':
        # Transpose of Matrix A
        result = [[0] * rows_A for _ in range(cols_A)]
        for i in range(rows_A):
            for j in range(cols_A):
                result[j][i] = A[i][j]
        print("\nTranspose of Matrix A:")
        print_matrix(result)

    elif choice == '5':
        # Transpose of Matrix B
        result = [[0] * rows_B for _ in range(cols_B)]
        for i in range(rows_B):
            for j in range(cols_B):
                result[j][i] = B[i][j]
        print("\nTranspose of Matrix B:")
        print_matrix(result)

    elif choice == '6':
        print("Exiting the program...")
        break
    else:
        print("Invalid choice. Please enter a number from 1 to 6.")


4a------------------------------------------------------------------------------------------------

# Function to perform Linear Search
def linear_search(roll_numbers, target):
    for i in range(len(roll_numbers)):
        if roll_numbers[i] == target:
            return i  # Target found, return the index
    return -1  # Target not found

# Function to perform Sentinel Search
def sentinel_search(roll_numbers, target):
    n = len(roll_numbers)
    last = roll_numbers[n - 1]  # Store the last element
    roll_numbers[n - 1] = target  # Replace the last element with target

    i = 0
    while roll_numbers[i] != target:
        i += 1

    roll_numbers[n - 1] = last  # Restore the last element

    if i < n - 1 or roll_numbers[n - 1] == target:
        return i  # Target found
    return -1  # Target not found

# Main program
roll_numbers = [23, 12, 5, 89, 34, 56, 10]  # Example roll numbers of students who attended training program

print("Roll numbers of students who attended the training program:", roll_numbers)

target = int(input("Enter roll number to search: "))

# Using Linear Search
index = linear_search(roll_numbers, target)
if index != -1:
    print(f"Student with roll number {target} attended the training program (Linear Search).")
else:
    print(f"Student with roll number {target} did not attend the training program (Linear Search).")

# Using Sentinel Search
index = sentinel_search(roll_numbers, target)
if index != -1:
    print(f"Student with roll number {target} attended the training program (Sentinel Search).")
else:
    print(f"Student with roll number {target} did not attend the training program (Sentinel Search).")

4b-----------------------------------------------------------------------------------------------------------------------------------------------------------

# Function to perform Binary Search
def binary_search(roll_numbers, target):
    low = 0
    high = len(roll_numbers) - 1

    while low <= high:
        mid = (low + high) // 2
        if roll_numbers[mid] == target:
            return mid  # Target found at mid index
        elif roll_numbers[mid] < target:
            low = mid + 1  # Search in the right half
        else:
            high = mid - 1  # Search in the left half
    return -1  # Target not found

# Function to perform Fibonacci Search
def fibonacci_search(roll_numbers, target):
    n = len(roll_numbers)
    fib_m_minus_2 = 0  # (m-2)th Fibonacci number
    fib_m_minus_1 = 1  # (m-1)th Fibonacci number
    fib_m = fib_m_minus_1 + fib_m_minus_2  # mth Fibonacci number

    while fib_m < n:
        fib_m_minus_2 = fib_m_minus_1
        fib_m_minus_1 = fib_m
        fib_m = fib_m_minus_1 + fib_m_minus_2

    offset = -1
    while fib_m > 1:
        i = min(offset + fib_m_minus_2, n-1)

        if roll_numbers[i] == target:
            return i  # Target found at index i
        elif roll_numbers[i] < target:
            fib_m = fib_m_minus_1
            fib_m_minus_1 = fib_m_minus_2
            fib_m_minus_2 = fib_m - fib_m_minus_1
            offset = i
        else:
            fib_m = fib_m_minus_2
            fib_m_minus_1 -= fib_m_minus_2
            fib_m_minus_2 = fib_m - fib_m_minus_1

    if fib_m_minus_1 and roll_numbers[offset + 1] == target:
        return offset + 1
    return -1  # Target not found

# Main program
roll_numbers = [5, 10, 12, 23, 34, 56, 89]  # Sorted roll numbers of students who attended the training program

print("Sorted roll numbers of students who attended the training program:", roll_numbers)

target = int(input("Enter roll number to search: "))

# Using Binary Search
index = binary_search(roll_numbers, target)
if index != -1:
    print(f"Student with roll number {target} attended the training program (Binary Search).")
else:
    print(f"Student with roll number {target} did not attend the training program (Binary Search).")

# Using Fibonacci Search
index = fibonacci_search(roll_numbers, target)
if index != -1:
    print(f"Student with roll number {target} attended the training program (Fibonacci Search).")
else:
    print(f"Student with roll number {target} did not attend the training program (Fibonacci Search).")

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

practical 5

def selection_sort(arr):
    n = len(arr)
    for i in range(n):
        min_idx = i
        for j in range(i + 1, n):
            if arr[j] < arr[min_idx]:
                min_idx = j
        arr[i], arr[min_idx] = arr[min_idx], arr[i]
    return arr

def bubble_sort(arr):
    n = len(arr)
    for i in range(n):
        for j in range(0, n - i - 1):
            if arr[j] > arr[j + 1]:
                arr[j], arr[j + 1] = arr[j + 1], arr[j]
    return arr

# Sample first-year percentages
percentages = [85.5, 90.2, 76.8, 88.0, 94.5, 78.2, 82.1, 89.0, 91.5, 77.5]

# Sorting using Selection Sort
sorted_selection = selection_sort(percentages.copy())
print("Sorted Percentages using Selection Sort:", sorted_selection)
print("Top 5 Scores (Selection Sort):", sorted_selection[-5:])

# Sorting using Bubble Sort
sorted_bubble = bubble_sort(percentages.copy())
print("Sorted Percentages using Bubble Sort:", sorted_bubble)
print("Top 5 Scores (Bubble Sort):", sorted_bubble[-5:])

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------
practical 6

def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)

# Sample first-year percentages
percentages = [85.5, 90.2, 76.8, 88.0, 94.5, 78.2, 82.1, 89.0, 91.5, 77.5]

# Sorting using Quick Sort
sorted_percentages = quick_sort(percentages)

# Display results
print("Sorted Percentages using Quick Sort:", sorted_percentages)
print("Top 5 Scores:", sorted_percentages[-5:])

------------------------------------------------------------------------------------------------------------------------------------------------------------

practical 7

#include<iostream>
#include<string>
using namespace std;

struct Node {
    string PRN;
    string name;
    Node* next;

    Node (string prn, string nm){
        PRN = prn;
        name = nm;
        next = nullptr;
    }
};

class club {
    private:
        Node* head;

    public:
        //constructor
        club(){
            head = nullptr;
        }

    // function to add member at the end

    void addmember(string prn, string nm){
        Node* newnode = new Node(prn, nm);
        if (head == nullptr){
            head = newnode;
        }else{
            Node* temp = head ;
            while (temp->next != nullptr){
                temp = temp->next;
            }
            temp->next = newnode;
        }
    }

    //function to delete member by prn (for president secretary and any other member )

    void deletemember(string prn){
        if (head == nullptr){
            cout<<"no member to delete "<<endl;
            return;
        }

        if (head->PRN == prn){
            Node* temp = head ;
            head = head->next;
            delete temp;
            return;
        }

        Node* temp = head ;
        while (temp->next != nullptr && temp->next->PRN != prn){
            temp = temp->next;
        }

        if (temp->next == nullptr){
            cout<<"member with PRN"<<prn<<"not found "<<endl;
        }
        else{
            Node* toDelete = temp->next;
            temp->next = temp->next->next;
            delete toDelete;
        }
    }

    //function to display all the members

    void displaymembers(){
        if (head == nullptr){
            cout<<"no members to display "<<endl;
            return;
        }

        Node* temp = head ;
        while(temp != nullptr){
            cout<<"PRN : "<<temp->PRN << "Name : "<<temp -> name<< endl;
            temp = temp->next;
        }
    }

   // Function to compute total number of members
    int totalmembers() {
        int count = 0;
        Node* temp = head;

        while (temp != nullptr) {
            count++;
            temp = temp->next;
    }

        return count; // Correctly return the count
}

    //function to concatenate two club lists

    void concatenate(club& otherclub){
        if (head == nullptr){
            head =  otherclub.head;
            return;
        }

        Node* temp = head ;
        while (temp-> next != nullptr ){
            temp = temp->next;
        }
        temp->next = otherclub.head;
    }

    //setting the head of the club for linking two clubs

    void sethead(Node* newhead){
        head = newhead;
    }

    //destructor for the free memory

    ~club(){
        Node* temp;
        while (head != nullptr ){
            temp = head;
            head = head->next;
            delete temp;
        }
    }


};

int main(){

    club division1;
    club division2;

    //adding members to division 1

    division1.addmember("prn1","rohan gorde");
    division1.addmember("prn2", "atharva");
    division1.addmember("prn3", "parth");

    //adding members to division 2:

    division2.addmember("prn1", "mrunal");
    division2.addmember("prn2", "bhagyashri");
    division2.addmember("prn3", "fanaa");

    //displaying division 1 members :

    cout<<"division 1 members "<<endl;
    division1.displaymembers();

    cout<<"\ndivision 2 members : "<<endl;
    division2.displaymembers();

    //concatenating division 1 to division 2

    division1.concatenate(division2);
    cout<<"\nafter concatenating division 2 members with the division 1 members ";
    division1.displaymembers();

    //compute the total numbers of members in division 1 after concatenation :

    cout<<"\ntotal members in division 1 after concatenation : "<<division1.totalmembers()<<endl;

    //deletting a member (fanaa)

    cout<<"\nafter deleting fanaa from the division : "<<endl;
    division1.displaymembers();

    return 0;
}
--------------------------------------------------------------------------------------------------------------------------------------------------------------
practical 8

#include <iostream>
#include <string>
using namespace std;

// Define the structure for a Node in the doubly linked list.
struct Node {
    int bit;        // Binary bit (0 or 1)
    Node* next;     // Pointer to the next node
    Node* prev;     // Pointer to the previous node

    // Constructor to initialize a new Node with the given bit value
    Node(int val) : bit(val), next(nullptr), prev(nullptr) {}
};

// Define the BinaryNumber class that represents a binary number as a doubly linked list.
class BinaryNumber {
private:
    Node* head;   // Head of the doubly linked list
    Node* tail;   // Tail of the doubly linked list

public:
    // Constructor initializes an empty binary number (no nodes yet).
    BinaryNumber() : head(nullptr), tail(nullptr) {}

    // Destructor to free up memory used by the linked list when the BinaryNumber object is destroyed.
    ~BinaryNumber() {
        Node* current = head;
        while (current != nullptr) {
            Node* temp = current;
            current = current->next;
            delete temp;
        }
    }

    // Function to insert a binary number from a string (e.g., "1011").
    void insertBinary(const string& bin) {
        for (char ch : bin) {
            int bit = (ch == '1') ? 1 : 0;  // Convert '1' or '0' to integer values 1 or 0.
            Node* newNode = new Node(bit);
            if (head == nullptr) {
                head = tail = newNode;  // First node, set both head and tail.
            } else {
                tail->next = newNode;  // Link the new node at the end.
                newNode->prev = tail;  // Set the previous pointer.
                tail = newNode;  // Move the tail to the new node.
            }
        }
    }

    // Function to display the binary number by traversing the list from head to tail.
    void display() const {
        Node* current = head;
        while (current != nullptr) {
            cout << current->bit;  // Print the bit stored in the current node.
            current = current->next;  // Move to the next node.
        }
        cout << endl;
    }

    // Function to compute the 1's complement: invert all bits (0 becomes 1, and 1 becomes 0).
    void onesComplement() {
        Node* current = head;
        while (current != nullptr) {
            current->bit = (current->bit == 1) ? 0 : 1;  // Flip the bit.
            current = current->next;
        }
    }

    // Function to compute the 2's complement: first compute 1's complement, then add 1.
    void twosComplement() {
        // First, calculate the 1's complement.
        onesComplement();

        // Now, add 1 to the 1's complement.
        Node* current = tail;
        int carry = 1;  // Start with carry = 1 to add.
        while (current != nullptr && carry) {
            int sum = current->bit + carry;
            current->bit = sum % 2;  // Set the new bit value (0 or 1).
            carry = sum / 2;  // Update carry (0 or 1).
            current = current->prev;  // Move to the previous node.
        }

        // If carry is still 1, insert a new node at the front of the list.
        if (carry) {
            Node* newNode = new Node(1);
            newNode->next = head;
            head->prev = newNode;
            head = newNode;
        }
    }

    // Function to add two binary numbers.
    BinaryNumber addBinary(const BinaryNumber& other) {
        BinaryNumber result;
        Node* ptr1 = this->tail;  // Start from the least significant bit (tail) of the first number.
        Node* ptr2 = other.tail;  // Start from the least significant bit (tail) of the second number.
        int carry = 0;  // Initialize carry.

        // Add bits starting from the least significant bit until both numbers are processed.
        while (ptr1 != nullptr || ptr2 != nullptr || carry) {
            int sum = carry;  // Start with the carry value.
            if (ptr1 != nullptr) {
                sum += ptr1->bit;  // Add the bit from the first binary number.
                ptr1 = ptr1->prev;  // Move to the previous bit.
            }
            if (ptr2 != nullptr) {
                sum += ptr2->bit;  // Add the bit from the second binary number.
                ptr2 = ptr2->prev;  // Move to the previous bit.
            }

            result.insertBinary(to_string(sum % 2));  // Store the result bit (sum modulo 2).
            carry = sum / 2;  // Update carry (sum divided by 2).
        }

        // Since the result is constructed from the least significant bit, we reverse it to get the correct order.
        result.reverse();

        return result;
    }

    // Function to reverse the binary number (needed after addition to correct the bit order).
    void reverse() {
        Node* current = head;
        Node* prev = nullptr;
        Node* next = nullptr;

        // Reverse the links between the nodes.
        while (current != nullptr) {
            next = current->next;
            current->next = prev;
            current->prev = next;
            prev = current;
            current = next;
        }
        head = prev;  // Update head to the new first node.
    }
};

// Main function to demonstrate the binary number operations.
int main() {
    // Create two binary numbers.
    BinaryNumber bin1;
    BinaryNumber bin2;

    // Insert binary numbers from strings.
    bin1.insertBinary("1101");  // Binary number: 1101 (13 in decimal)
    bin2.insertBinary("1011");  // Binary number: 1011 (11 in decimal)

    // Display binary numbers.
    cout << "Binary Number 1: ";
    bin1.display();
    cout << "Binary Number 2: ";
    bin2.display();

    // Compute and display 1's complement of the first binary number.
    cout << "1's complement of Binary Number 1: ";
    bin1.onesComplement();
    bin1.display();

    // Reset bin1 and compute 2's complement.
    bin1.insertBinary("1101");  // Reset bin1 to the original value.
    cout << "2's complement of Binary Number 1: ";
    bin1.twosComplement();
    bin1.display();

    // Add two binary numbers and display the result.
    BinaryNumber result = bin1.addBinary(bin2);
    cout << "Addition of Binary Number 1 and Binary Number 2: ";
    result.display();

    return 0;
}

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------
practical 9

#include<iostream>
#include<stack>
#include<cctype>
#include<string>
using namespace std;

//function to cleanup the string

string cleanstring(const string& input){
    string cleaned = "";
    for (char c : input){
        if (isalnum(c)){
            cleaned += tolower(c);
        }
    }
    return cleaned;
}

//function to return original string and reversed string using stack :

void printoriginalandreversed(const string& input){
    string cleaned = cleanstring(input);

//print the cleaned original string

    cout<<"original cleaned string "<<cleaned<<endl;

//use stack to reverse the string

stack<char> s;
for (char c : cleaned){
    s.push(c); //push charecter onto the stack
}

string reversed = "";
while(!s.empty()){
    reversed += s.top();
    s.pop();
}
//print the reversed string :

cout<<"reversed string : "<<reversed<<endl;
}

//function to check whether a string is a palidrome

bool ispalindrome(const string& input){
    string cleaned = cleanstring(input);

    //use stack to reverse the string :

    stack<char>s;
    for (char c : cleaned){
        s.push(c);
    }

    string reversed = "";
    while(!s.empty()){
        reversed += s.top();
        s.pop();
    }

    //check if the original cleaned string is equal to the reversed string :
    return cleaned == reversed;
}

int main(){
    string input;

    //asking user to input a string :

    cout<<"enter a string : "<<endl;
    getline(cin,input);

    //print original and reversed string using stack :
    printoriginalandreversed(input);

    //check if the given string is a plindrome :

    if (ispalindrome(input)){
        cout<<"the string is a palindrome "<<endl;
    }
    else{
        cout<<"the string is not a palindrome "<<endl;
    }
    return 0 ;
}

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

practical 10


#include <iostream>
#include <stack>
#include <string>
#include <cctype>
#include <cmath>

using namespace std;

// Function to determine the precedence of operators
int precedence(char op) {
    if (op == '+' || op == '-') {
        return 1;
    } else if (op == '*' || op == '/') {
        return 2;
    }
    return 0;
}

// Function to perform arithmetic operations
int applyOperator(int a, int b, char op) {
    switch (op) {
        case '+': return a + b;
        case '-': return a - b;
        case '*': return a * b;
        case '/': return a / b;
        default: return 0;
    }
}

// Function to convert infix to postfix
string infixToPostfix(const string &infix) {
    stack<char> operators;
    string postfix = "";

    for (char c : infix) {
        if (isdigit(c)) {
            postfix += c;  // Append operands to the result
        } else if (c == '(') {
            operators.push(c);  // Push '(' to stack
        } else if (c == ')') {
            while (!operators.empty() && operators.top() != '(') {
                postfix += operators.top();
                operators.pop();
            }
            operators.pop();  // Pop '(' from stack
        } else if (c == '+' || c == '-' || c == '*' || c == '/') {
            while (!operators.empty() && precedence(operators.top()) >= precedence(c)) {
                postfix += operators.top();
                operators.pop();
            }
            operators.push(c);  // Push current operator to stack
        }
    }

    // Pop all remaining operators in the stack
    while (!operators.empty()) {
        postfix += operators.top();
        operators.pop();
    }

    return postfix;
}

// Function to evaluate the postfix expression
int evaluatePostfix(const string &postfix) {
    stack<int> operands;

    for (char c : postfix) {
        if (isdigit(c)) {
            operands.push(c - '0');  // Convert character to integer and push onto stack
        } else if (c == '+' || c == '-' || c == '*' || c == '/') {
            int b = operands.top(); operands.pop();
            int a = operands.top(); operands.pop();
            int result = applyOperator(a, b, c);
            operands.push(result);  // Push the result back onto the stack
        }
    }

    return operands.top();  // The final result is the only value left in the stack
}

int main() {
    string infix;
    cout << "Enter an infix expression (with single-character operands and operators): ";
    cin >> infix;

    string postfix = infixToPostfix(infix);
    cout << "Postfix expression: " << postfix << endl;

    int result = evaluatePostfix(postfix);
    cout << "Evaluation result: " << result << endl;

    return 0;
}


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

practical 11


#include<iostream>
#include<queue>
#include<string>
using namespace std;

//function to add the job in the queue :

void addjob(queue <string>& jobqueue, const string& job){
    jobqueue.push(job);
    cout<<"job added : "<<job<<endl;
}

//function to delete a job from a queue :

void deletejob(queue <string>& jobqueue){
   if (jobqueue.empty()){
    cout<<"no jobs in the queue to delete "<<endl;
   }
   else{
    cout<<"processing jobs : "<<jobqueue.front()<<endl;
    jobqueue.pop();
   }
}

//function to display the current jobs in the queue :

void displayqueue(const queue<string>& jobqueue){
    if (jobqueue.empty()){
        cout<<"no jobs in the queue "<<endl;
    }
    else{
        cout<<"current jobs in the queue : "<<endl;
        queue<string> tempqueue = jobqueue;
        while(!tempqueue.empty()){
            cout<<tempqueue.front()<<endl;
            tempqueue.pop();
        }
    }
}

int main(){
    queue<string> jobqueue;
    int choise;
    string job;

    while(true){
        //menu for the user input :

        cout<<"\nJob queue simulator : "<<endl;
        cout<<"1. add job to the queue : "<<endl;
        cout<<"2. delete job from the queue : "<<endl;
        cout<<"3. display all the jobs in the queue : "<<endl;
        cout<<"4. exit "<<endl;

        cout<<"\n Enter your choise : "<<endl;
        cin>>choise;
        cin.ignore();

        switch(choise){
            case 1 :
            cout<<"enter a job description : "<<endl;
            getline(cin, job);
            addjob(jobqueue, job);
            break;

            case 2:
            deletejob(jobqueue);
            break;

            case 3:
            displayqueue(jobqueue);
            break;

            case 4:
            cout<<"\n exiting the program : "<<endl;
            return 0;

            default:
            cout<<"invalid choise . please try again : "<<endl;
        }
    }


    return 0;
}
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

practical 12


#include <iostream>
using namespace std;

class Deque {
private:
    int* arr;             // Array to store the deque elements
    int front, rear;      // Front and rear pointers
    int size;             // Maximum size of the deque
    int currentSize;      // Current number of elements in the deque

public:
    // Constructor to initialize the deque
    Deque(int s) {
        size = s;
        arr = new int[size];
        front = -1;
        rear = -1;
        currentSize = 0;
    }

    // Destructor to free dynamically allocated memory
    ~Deque() {
        delete[] arr;
    }

    // Function to check if the deque is empty
    bool isEmpty() {
        return currentSize == 0;
    }

    // Function to check if the deque is full
    bool isFull() {
        return currentSize == size;
    }

    // Function to add an element at the front of the deque
    void addFront(int value) {
        if (isFull()) {
            cout << "Deque is full, cannot add element at the front." << endl;
        } else {
            if (front == -1) {
                front = 0;
                rear = 0;
            } else if (front == 0) {
                front = size - 1;
            } else {
                front--;
            }
            arr[front] = value;
            currentSize++;
            cout << "Added " << value << " at the front." << endl;
        }
    }

    // Function to add an element at the rear of the deque
    void addRear(int value) {
        if (isFull()) {
            cout << "Deque is full, cannot add element at the rear." << endl;
        } else {
            if (rear == -1) {
                front = 0;
                rear = 0;
            } else {
                rear = (rear + 1) % size;
            }
            arr[rear] = value;
            currentSize++;
            cout << "Added " << value << " at the rear." << endl;
        }
    }

    // Function to delete an element from the front of the deque
    void deleteFront() {
        if (isEmpty()) {
            cout << "Deque is empty, cannot delete from the front." << endl;
        } else {
            cout << "Deleted " << arr[front] << " from the front." << endl;
            if (front == rear) {
                front = -1;
                rear = -1;
            } else {
                front = (front + 1) % size;
            }
            currentSize--;
        }
    }

    // Function to delete an element from the rear of the deque
    void deleteRear() {
        if (isEmpty()) {
            cout << "Deque is empty, cannot delete from the rear." << endl;
        } else {
            cout << "Deleted " << arr[rear] << " from the rear." << endl;
            if (front == rear) {
                front = -1;
                rear = -1;
            } else {
                rear = (rear - 1 + size) % size;
            }
            currentSize--;
        }
    }

    // Function to display the current elements in the deque
    void display() {
        if (isEmpty()) {
            cout << "Deque is empty." << endl;
        } else {
            cout << "Deque elements: ";
            int i = front;
            while (i != rear) {
                cout << arr[i] << " ";
                i = (i + 1) % size;
            }
            cout << arr[rear] << endl;
        }
    }
};

int main() {
    int size;
    cout << "Enter the size of the deque: ";
    cin >> size;

    Deque dq(size);

    int choice, value;

    while (true) {
        cout << "\nDeque Operations Menu\n";
        cout << "1. Add element at the front\n";
        cout << "2. Add element at the rear\n";
        cout << "3. Delete element from the front\n";
        cout << "4. Delete element from the rear\n";
        cout << "5. Display the deque\n";
        cout << "6. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter value to add at the front: ";
                cin >> value;
                dq.addFront(value);
                break;
            case 2:
                cout << "Enter value to add at the rear: ";
                cin >> value;
                dq.addRear(value);
                break;
            case 3:
                dq.deleteFront();
                break;
            case 4:
                dq.deleteRear();
                break;
            case 5:
                dq.display();
                break;
            case 6:
                cout << "Exiting program.\n";
                return 0;
            default:
                cout << "Invalid choice. Please try again.\n";
        }
    }

    return 0;
}

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

practical 13


#include <iostream>
#include <string>
using namespace std;

class PizzaParlor {
private:
    string* orders;     // Array to store orders
    int front, rear;    // Front and rear pointers
    int size;           // Maximum size of the queue (maximum orders)
    int currentSize;    // Current number of orders in the queue

public:
    // Constructor to initialize the circular queue
    PizzaParlor(int maxOrders) {
        size = maxOrders;
        orders = new string[size];
        front = -1;
        rear = -1;
        currentSize = 0;
    }

    // Destructor to free dynamically allocated memory
    ~PizzaParlor() {
        delete[] orders;
    }

    // Function to check if the queue is empty
    bool isEmpty() {
        return currentSize == 0;
    }

    // Function to check if the queue is full
    bool isFull() {
        return currentSize == size;
    }

    // Function to add an order to the queue
    void addOrder(const string& order) {
        if (isFull()) {
            cout << "Sorry, the pizza parlor is full. Cannot accept more orders." << endl;
        } else {
            if (front == -1) {  // If the queue is empty, set both front and rear to 0
                front = 0;
                rear = 0;
            } else {
                // Circular increment of rear
                rear = (rear + 1) % size;
            }
            orders[rear] = order;
            currentSize++;
            cout << "Order added: " << order << endl;
        }
    }

    // Function to serve (delete) an order from the front of the queue
    void serveOrder() {
        if (isEmpty()) {
            cout << "No orders to serve, the pizza parlor is empty." << endl;
        } else {
            cout << "Serving order: " << orders[front] << endl;
            if (front == rear) {  // Only one order in the queue
                front = -1;
                rear = -1;
            } else {
                // Circular increment of front
                front = (front + 1) % size;
            }
            currentSize--;
        }
    }

    // Function to display all orders in the queue
    void displayOrders() {
        if (isEmpty()) {
            cout << "No orders to display, the pizza parlor is empty." << endl;
        } else {
            cout << "Current orders in the pizza parlor: " << endl;
            int i = front;
            while (i != rear) {
                cout << orders[i] << endl;
                i = (i + 1) % size;
            }
            cout << orders[rear] << endl;  // Display the last order
        }
    }
};

int main() {
    int maxOrders;
    cout << "Enter the maximum number of orders the pizza parlor can accept: ";
    cin >> maxOrders;

    PizzaParlor parlor(maxOrders);

    int choice;
    string order;

    while (true) {
        cout << "\nPizza Parlor Menu\n";
        cout << "1. Add order\n";
        cout << "2. Serve order\n";
        cout << "3. Display all orders\n";
        cout << "4. Exit\n";
        cout << "Enter your choice: ";
        cin >> choice;
        cin.ignore();  // To clear the input buffer

        switch (choice) {
            case 1:
                cout << "Enter order details: ";
                getline(cin, order);  // Get the order details
                parlor.addOrder(order);
                break;
            case 2:
                parlor.serveOrder();
                break;
            case 3:
                parlor.displayOrders();
                break;
            case 4:
                cout << "Exiting the program.\n";
                return 0;  // Exit the program
            default:
                cout << "Invalid choice. Please try again.\n";
        }
    }

    return 0;
}
