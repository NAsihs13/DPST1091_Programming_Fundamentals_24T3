Week 11 Tutorial Questions
# Programming linked lists with multi file systems

Given the starter code:

main.c: used to test the functions implemented in linked_lists.c

linked_lists.h: contains defined function prototypes for the functions that will be implemented in linked_lists.c

linked_lists.c: implementation file, containing stubs of functions to be implemented

we will implement functions to create a node, insert a node at the tail of a linked list, insert a node at the head of a linked list and find the length of a linked list.

Given code:
linked_lists.h
```C
// linked_lists.h
// This program was written by Sofia De Bellis (z5418801), on March 2024
// Header file for simple linked lists functions

struct node {
    // The data stored in the node
    int data;
    // Pointer to the next node in the linked list
    struct node *next;
};

// Creates a new node
//
// Parameters:
//      data: The data to be stored in the new node
//
// Returns:
//      A pointer to the new node
struct node *create_node(int data);

// Inserts a new node at the head of a linked list
//
// Parameters:
//      head: A pointer to the head of the linked list
//      data: The data to be stored in the new node
//
// Returns:
//      A pointer to the new head of the linked list
struct node *insert_head(struct node *head, int data);

// Inserts a new node at the tail of a linked list
//
// Parameters:
//      head: A pointer to the head of the linked list
//      data: The data to be stored in the new node
//
// Returns:
//      A pointer to the head of the linked list
struct node *insert_tail(struct node *head, int data);

// Traverses a linked list and prints the data in each node
//
// Parameters:
//      head: A pointer to the head of the linked list
//
// Returns:
//      None
void print_list(struct node *head);

// Finds the number of nodes in a linked list
//
// Parameters:
//      head: A pointer to the head of the linked list
//
// Returns:
//      The number of nodes in the linked list
int list_length(struct node *head);
```

linked_lists.c
```C
// linked_list.c
// This program was written by YOUR-NAME (zID)
// Implementation for simple linked lists functions

#include <stdio.h>
#include <stdlib.h>

#include "linked_lists.h"

struct node *create_node(int data) {
    // TODO
    exit(1);
}

struct node *insert_head(struct node *head, int data) {
    // TODO
    exit(1);
}

struct node *insert_tail(struct node *head, int data) {
    // TODO
    exit(1);
}

void print_list(struct node *head) {
    // Set current to be the first node in the list
    struct node *current = head;
    
    // Traverse the linked list and print each node 
    // until we reach the end of the list
    while (current != NULL) {
        printf("%d -> ", current->data);
        current = current->next;
    }
    printf("X\n");
}

int list_length(struct node *head) {
    // TODO
    exit(1);
}
```

main.c

```C
// main.c
// This program was written by YOUR-NAME (zID)
// // Program to test linked lists functions

#include <stdio.h>
#include <stdlib.h>

#include "linked_lists.h"

int main(void) {

    // Create a pointer to the head of the linked list
    struct node *head = NULL;

    // Insert a node at the beginning of the linked list
    head = insert_head(head, 10);

    // Insert a node at the beginning of the linked list
    head = insert_head(head, 5);

    // Insert a node at the end of the linked list
    head = insert_tail(head, 15);

    // Insert a node at the end of the linked list
    head = insert_tail(head, 20);

    // Print the linked list
    print_list(head);

    // Calculate and print the length of the linked list
    int length = list_length(head);
    printf("There are %d nodes in the list\n", length);

    return 0;
}
```

Next: Let' s do it step by step.

step 1: initialize a new node
```C
struct node *create_node(int data) {
    struct node *new_node = malloc(sizeof(struct node));
    new_node->data = data;
    new_node->next = NULL;
    return new_node;
}
```

step 2: insert node
```C
struct node *insert_head(struct node *head, int data) {
    struct node *new_head = create_node(data);
    new_head->next = head;
    return new_head;
}
```

step 3: insert tail
```C
struct node *insert_tail(struct node *head, int data) {
    struct node *new_node = create_node(data);
    if (head == NULL) {
        return new_node;
    }

    // tranverse -> until find the last element

    struct node *current = head;
    while(current->next != NULL){
        current = current->next;
    }

    // Link the Last Node to the New Node

    current->next = new_node;
    return head;
}
```

step 4: list_length
```C
int list_length(struct node *head) {
    int length = 0;
    struct node *current = head;

    // the same : tranverse, and count the number;

    while(current != NULL) {
        length++;
        current = current->next;
    }
    return length;
}
```
