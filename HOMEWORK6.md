### 1. Implement Stack Using:
```cpp
(i) Array Implementation
```cpp

#include <iostream>
using namespace std;

class Stack {
    int top;
    int arr[1000]; // Fixed-size array
public:
    Stack() { top = -1; }

    void push(int x) {
        if (top >= 999) {
            cout << "Stack Overflow" << endl;
            return;
        }
        arr[++top] = x;
    }

    int pop() {
        if (top == -1) {
            cout << "Stack Underflow" << endl;
            return -1;
        }
        return arr[top--];
    }

    int peek() {
        if (top == -1) {
            cout << "Stack is Empty" << endl;
            return -1;
        }
        return arr[top];
    }

    bool isEmpty() {
        return top == -1;
    }
};

(ii) Dynamic Array Implementation
```cpp

#include <iostream>
using namespace std;

class Stack {
    int *arr;
    int top;
    int capacity;

public:
    Stack(int size = 100) {
        arr = new int[size];
        capacity = size;
        top = -1;
    }

    void push(int x) {
        if (top == capacity - 1) {
            // Resize the array
            int *newArr = new int[2 * capacity];
            for (int i = 0; i < capacity; i++) {
                newArr[i] = arr[i];
            }
            delete[] arr;
            arr = newArr;
            capacity *= 2;
        }
        arr[++top] = x;
    }

    int pop() {
        if (top == -1) {
            cout << "Stack Underflow" << endl;
            return -1;
        }
        return arr[top--];
    }

    int peek() {
        if (top == -1) {
            cout << "Stack is Empty" << endl;
            return -1;
        }
        return arr[top];
    }

    bool isEmpty() {
        return top == -1;
    }

    ~Stack() {
        delete[] arr;
    }
};


(iii) Linked List Implementation

```cpp
#include <iostream>
using namespace std;

struct Node {
    int data;
    Node* next;
};

class Stack {
    Node* top;
public:
    Stack() { top = nullptr; }

    void push(int x) {
        Node* temp = new Node();
        if (!temp) {
            cout << "Stack Overflow" << endl;
            return;
        }
        temp->data = x;
        temp->next = top;
        top = temp;
    }

    int pop() {
        if (!top) {
            cout << "Stack Underflow" << endl;
            return -1;
        }
        int x = top->data;
        Node* temp = top;
        top = top->next;
        delete temp;
        return x;
    }

    int peek() {
        if (!top) {
            cout << "Stack is Empty" << endl;
            return -1;
        }
        return top->data;
    }

    bool isEmpty() {
        return top == nullptr;
    }
};

