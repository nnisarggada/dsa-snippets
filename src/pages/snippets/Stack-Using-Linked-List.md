---
extension: cpp
layout: "../../layouts/SubmissionLayout.astro"
title: Stack Using Linked List
---

```cpp
#include <iostream>
using namespace std;

class node;
node* top = NULL;

class node {
public:
  int data;
  node *next;

  node* create_node(){
    node *temp = new(node);
    temp->next = NULL;
    return temp;
  }

  void push(int data) {
    node *temp = create_node();
    temp->data = data;
    temp->next = top;
    top = temp;
  }
  void pop() {
    if (top == NULL) {
      cout << "Stack is empty" << endl;
      return;
    }
    node *temp = top;
    top = top->next;
    delete(temp);
  }

  void peek() {
    if (top == NULL) {
      cout << "Stack is empty" << endl;
      return;
    }
    cout << top->data << endl;
  }
};

int main() {
  node stack;
  int choice = 0;
  while (choice != 4) {
    cout << "1. Push" << endl;
    cout << "2. Pop" << endl;
    cout << "3. Peek" << endl;
    cout << "4. Exit" << endl;
    cout << "Enter your choice: ";
    cin >> choice;
    switch (choice) {
      case 1:
        int data;
        cout << "Enter data: ";
        cin >> data;
        stack.push(data);
        break;
      case 2:
        stack.pop();
        break;
      case 3:
        stack.peek();
        break;
      case 4:
        exit(0);
        break;
      default:
        cout << "Invalid choice" << endl;
    }
  }
  return 0;
}
```
