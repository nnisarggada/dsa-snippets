---
extension: cpp
layout: "../../layouts/SubmissionLayout.astro"
title: Binary Search Tree
---

```cpp
#include <iostream>
using namespace std;

class node{
  public:
    int data;
    node* left;
    node* right;

    node* create_node(){
      node* new_node = new(node);
      new_node->left = NULL;
      new_node->right = NULL;
      return new_node;
    }

    node* insert(node* root, int data){
      if (root == NULL){
        node* new_node = create_node();
        new_node->data = data;
        return new_node;
      }
      if (data < root->data){
        root->left = insert(root->left, data);
      }
      else{
        root->right = insert(root->right, data);
      }
      return root;
    }

    void search(node* root, int data){
      if (root == NULL){
        cout << "Not Found" << endl;
        return;
      }
      if (data < root->data){
        search(root->left, data);
      }
      else if (data > root->data){
        search(root->right, data);
      }
      else{
        cout << "Found " << root->data << endl;
      }
    }

    void inorder(node* root){
      if (root == NULL){
        cout << endl;
        return;
      }
      inorder(root->left);
      cout << root->data << " ";
      inorder(root->right);
    }

    void preorder(node* root){
      if (root == NULL){
        cout << endl;
        return;
      }
      cout << root->data << " ";
      preorder(root->left);
      preorder(root->right);
    }

    void postorder(node* root){
      if (root == NULL){
        cout << endl;
        return;
      }
      postorder(root->left);
      postorder(root->right);
      cout << root->data << " ";
    }

    void find_largest(node* root){
      if (root == NULL){
        return;
      }
      if (root->right == NULL){
        cout << "Largest: " << root->data << endl;
        return;
      }
      find_largest(root->right);
    }

    void find_smallest(node* root){
      if (root == NULL){
        return;
      }
      if (root->left == NULL){
        cout << "Smallest: " << root->data << endl;
        return;
      }
      find_smallest(root->left);
    }
};

int main()
{
  int choice;
  node* root = NULL;

  while (choice != 8){
    cout << endl;
    cout << "1. Insert" << endl;
    cout << "2. Search" << endl;
    cout << "3. Inorder" << endl;
    cout << "4. Preorder" << endl;
    cout << "5. Postorder" << endl;
    cout << "6. Largest" << endl;
    cout << "7. Smallest" << endl;
    cout << "8. Exit" << endl;
    cout << "Enter your choice: ";
    cin >> choice;
    cout << endl;

    int data;

    switch (choice){
      case 1:
        cout << "Enter data to insert: ";
        cin >> data;
        root = root->insert(root, data);
        break;
      case 2:
        cout << "Enter data to search: ";
        cin >> data;
        root->search(root, data);
        break;
      case 3:
        cout << "Inorder: ";
        root->inorder(root);
        break;
      case 4:
        cout << "Preorder: ";
        root->preorder(root);
        break;
      case 5:
        cout << "Postorder: ";
        root->postorder(root);
        break;
      case 6:
        root->find_largest(root);
        break;
      case 7:
        root->find_smallest(root);
        break;
      case 8:
        break;
      default:
        cout << "Invalid choice" << endl;
        break;
    }
  }

  return 0;
}
```
