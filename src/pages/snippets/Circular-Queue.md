---
extension: cpp
layout: "../../layouts/SubmissionLayout.astro"
title: Circular Queue
---

```cpp
#include <iostream>
using namespace std;

#define size 5

class CircularQueue {
    public:
        int a[size];
        int front = -1;
        int rear = -1;

        bool underflow(){
            return front == -1;
        }

        bool overflow(){
            return (front == rear + 1 || (front == 0 && rear == size - 1));
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
            rear = rear % size;
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
                front = front % size;
            }
        }

        void display(){
            if (underflow()){
                cout << "Queue is empty" << endl;
                return;
            }
            cout << "The Queue is: ";
            if (front <= rear){
                for (int i = front; i <= rear; i++){
                    cout << a[i] << " ";
                }
            }
            else {
                for (int i = front; i < size; i++){
                    cout << a[i] << " ";
                }
                for (int i = 0; i <= rear; i++){
                    cout << a[i] << " ";
                }
            }
        }
};
```
