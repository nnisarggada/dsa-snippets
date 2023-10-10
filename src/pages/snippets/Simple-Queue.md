---
extension: cpp
layout: "../../layouts/SubmissionLayout.astro"
title: Simple Queue
---

```cpp
#include <iostream>
using namespace std;

#define size 100

class SimpleQueue {
    public:
        int a[size];
        int front = -1;
        int rear = -1;

        bool underflow(){
            return front == -1;
        }

        bool overflow(){
            return rear == size - 1;
        }

        void enqueue(int x){
            if (overflow()){
                cout << "Queue is full" << endl;
                return;
            }
            if (front == -1){
                front++;
            }
            rear++;
            a[rear] = x;
        }

        void dequeue(){
            if (underflow()){
                cout << "Queue is empty" << endl;
                return;
            }
            cout << "Element deleted is " << a[front] << endl;
            if (rear == front){
                rear = -1;
                front = -1;
            }
            else {
                front++;
            }
        }

        void display(){
            if (underflow()){
                cout << "Queue is empty" << endl;
                return;
            }
            cout << "The Queue is: ";
            for (int i = front; i <= rear; i++){
                cout << a[i] << " ";
            }
        }
};
```
