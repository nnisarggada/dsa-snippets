---
extension: cpp
layout: "../../layouts/SubmissionLayout.astro"
title: Depth First Search
---

```cpp
// Depth First Search
#include <iostream>
using namespace std;

#define size 10

class Stack {
  int arr[size];
  int top = -1;

public:

  bool underflow(){
    return top == -1;
  }

  bool overflow(){
    return top == size - 1;
  }

  void push(int data){
    if(overflow()){
      cout<<"Stack is full"<<endl;
    }
    else{
      top++;
      arr[top] = data;
    }
  };

  int pop(){
    if(underflow()){
      cout<<"Stack is empty"<<endl;
      return -1;
    }
    else{
      int x = arr[top];
      top--;
      return x;
    }
  }
};

void dfs(int n, int mat[size][size], int src){
  Stack s;
  int visited[size] = {0};

  s.push(src);
  visited[src] = 1;

  while (!s.underflow()) {
    int u = s.pop();
    cout << u << " ";
    for (int i = 0; i < n; i++) {
      if (mat[u][i] == 1 && visited[i] == 0) {
        s.push(i);
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

  dfs(n, mat, src);

  return 0;
}
```
