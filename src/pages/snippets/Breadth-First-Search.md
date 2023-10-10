---
extension: cpp
layout: "../../layouts/SubmissionLayout.astro"
title: Breadth First Search
---

```cpp
// Breadth First Search
#include <iostream>
using namespace std;

#define size 10

class Queue {
  int arr[size];
  int front = -1;
  int rear = -1;

public:

  bool underflow(){
    return front == -1;
  }

  bool overflow(){
    return rear == size - 1;
  }

  void enqueue(int data){
    if(overflow()){
      cout<<"Queue is full"<<endl;
    }
    else{
      if(front == -1){
        front++;
      }
      rear++;
      arr[rear] = data;
    }
  };

  int dequeue(){
    if(underflow()){
      cout<<"Queue is empty"<<endl;
      return -1;
    }
    else{
      int x = arr[front];
      if(front == rear){
        front = -1;
        rear = -1;
      }
      else{
        front++;
      }
      return x;
    }
  }
};

void bfs(int n, int mat[size][size], int src){
  Queue q;
  int visited[size] = {0};

  q.enqueue(src);
  visited[src] = 1;

  while (!q.underflow()) {
    int u = q.dequeue();
    cout << u << " ";
    for (int i = 0; i < n; i++) {
      if (mat[u][i] == 1 && visited[i] == 0) {
        q.enqueue(i);
        visited[i] = 1;
      }
    }
  }
};

int main()
{
  int n;
  cout << "Enter the number of vertices: ";
  cin >> n;

  int mat[size][size];
  cout << "Enter the adjacency matrix: " << endl;
  for (int i = 0; i < n; i++) {
    for (int j = 0; j < n; j++) {
      cin >> mat[i][j];
    }
  }

  int src;
  cout << "Enter the source vertex: ";
  cin >> src;

  bfs(n, mat, src);

  return 0;
}
```
