---
extension: cpp
layout: "../../layouts/SubmissionLayout.astro"
title: Queue Using Linked List
---

```cpp
#include <iostream>
using namespace std;

class node;
node* front = NULL;
node* rear = NULL;

class node {
  public:
    int data;
    node* next;

  node* create_node(){
    node* new_node = new(node);
    new_node->next = NULL;
    return new_node;
  };

  void enqueue(int data){
    node* new_node = create_node();
    new_node->data = data;
    if (front == NULL) {
      front = new_node;
      rear = new_node;
    } else {
      rear->next = new_node;
      rear = new_node;
    }
  }

  void dequeue(){
    if (front == NULL) {
      cout << "Queue is empty" << endl;
    } else {
      node* temp = front;
      front = front->next;
      delete(temp);
    }
  }

  void display(){
    node* temp = front;
    while (temp != NULL) {
      cout << temp->data << " ";
      temp = temp->next;
    }
    cout << endl;
  }

};

int main() {
  node queue;
  int choice = 0;
  while (choice != 4) {

    cout << "1. Enqueue" << endl;
    cout << "2. Dequeue" << endl;
    cout << "3. Display" << endl;
    cout << "4. Exit" << endl;
    cin >> choice;

    switch (choice) {
      case 1:
        int data;
        cout << "Enter data: ";
        cin >> data;
        queue.enqueue(data);
        break;
      case 2:
        queue.dequeue();
        break;
      case 3:
        queue.display();
        break;
      case 4:
        exit(0);
        break;
      default:
        cout << "Invalid choice" << endl;
    }
  }
}
```
