# 24AD303 DATA STRUCTURE & ALGORITHMS: LAB RECORD

## INDEX

| S.No | Name of the Program | Section |
| ---- | ------------------- | ------- |
| 1 | Array implementation of List, Stack and Queue ADTs. | Ex 1a, 1b, 1c |
| 2 | Implementation of Singly Linked List. | Ex 2 |
| 3 | Write a program to simulate the working of stack using an array with the following: i) Push ii) Pop iii) Display. The program should print appropriate messages for stack overflow, stack underflow. | Same program as Ex 1b |
| 4 | Linked list implementation of Linear Queue ADTs. | Ex 4 |
| 5 | Implementation of Polynomial addition and multiplication using Linked list. | Ex 5 |
| 6 | Implementation of Binary Search Trees. | Ex 6 |
| 7 | Implementation of Dijkstra's Algorithm. | Ex 7 |
| 8 | Implementation of Prim's Algorithm. | Ex 8 |
| 9 | Implementation of Linear Search and Binary Search. | Ex 9a, 9b |
| 10 | Implementation of Insertion Sort and Selection Sort | Ex 10a,
## Ex. No: 1a ARRAY IMPLEMENTATION OF LIST

**Aim:**
To create a list using an array and perform create, insert, delete, search and display operations.

**Algorithm:**
1. Start
2. Define an array `a` of size MAX and set `n = 0` (number of elements)
3. Display the menu: 1.CREATE 2.INSERT 3.DELETE 4.SEARCH 5.DISPLAY 6.EXIT
4. Read the choice
5. If choice = 1 (CREATE)
   - Read the number of elements `n`. If `n > MAX`, print an error
   - Else read `n` elements into the array
6. If choice = 2 (INSERT)
   - If `n == MAX`, print "List is full"
   - Read position `pos` and element `val`. If `pos < 0` or `pos > n`, print "Invalid position"
   - Else shift elements from `a[n-1]` down to `a[pos]` one position right
   - Store `val` at `a[pos]` and increment `n`
7. If choice = 3 (DELETE)
   - If `n == 0`, print "List is empty"
   - Read position `pos`. If `pos < 0` or `pos >= n`, print "Invalid position"
   - Else print the deleted element, shift elements from `a[pos+1]` to `a[n-1]` one position left and decrement `n`
8. If choice = 4 (SEARCH), read the key, compare it with each element and print its position, or "Element not found"
9. If choice = 5 (DISPLAY), print `a[0]` to `a[n-1]`
10. If choice = 6, stop. Otherwise repeat from step 3.

**Program:**
```c
#include <stdio.h>
#define MAX 10

int a[MAX], n = 0;

void create() {
    printf("Enter number of elements: ");
    scanf("%d", &n);
    if (n > MAX) { printf("Maximum size is %d\n", MAX); n = 0; return; }
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
}

void insert() {
    int pos, val;
    if (n == MAX) { printf("List is full\n"); return; }
    printf("Enter position and element: ");
    scanf("%d %d", &pos, &val);
    if (pos < 0 || pos > n) { printf("Invalid position\n"); return; }
    for (int i = n; i > pos; i--)
        a[i] = a[i - 1];
    a[pos] = val;
    n++;
}

void delete() {
    int pos;
    if (n == 0) { printf("List is empty\n"); return; }
    printf("Enter position: ");
    scanf("%d", &pos);
    if (pos < 0 || pos >= n) { printf("Invalid position\n"); return; }
    printf("Deleted %d\n", a[pos]);
    for (int i = pos; i < n - 1; i++)
        a[i] = a[i + 1];
    n--;
}

void search() {
    int key;
    printf("Enter element to search: ");
    scanf("%d", &key);
    for (int i = 0; i < n; i++)
        if (a[i] == key) { printf("Found at position %d\n", i); return; }
    printf("Element not found\n");
}

void display() {
    printf("List: ");
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
}

int main() {
    int ch;
    while (1) {
        printf("\n1.CREATE 2.INSERT 3.DELETE 4.SEARCH 5.DISPLAY 6.EXIT\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1: create(); break;
            case 2: insert(); break;
            case 3: delete(); break;
            case 4: search(); break;
            case 5: display(); break;
            case 6: return 0;
            default: printf("Invalid choice\n");
        }
    }
}
```

**Output:**
```
1.CREATE 2.INSERT 3.DELETE 4.SEARCH 5.DISPLAY 6.EXIT
Enter choice: 1
Enter number of elements: 3
Enter 3 elements: 10 20 30

Enter choice: 5
List: 10 20 30

Enter choice: 2
Enter position and element: 1 15

Enter choice: 5
List: 10 15 20 30

Enter choice: 3
Enter position: 2
Deleted 20

Enter choice: 5
List: 10 15 30

Enter choice: 4
Enter element to search: 30
Found at position 2

Enter choice: 4
Enter element to search: 99
Element not found

Enter choice: 3
Enter position: 7
Invalid position

Enter choice: 6
```

**Result:**
Thus the program to implement a list using an array was executed and create, insert, delete, search and display operations were verified successfully.

## Ex. No: 1b / 3 ARRAY IMPLEMENTATION OF STACK

**Aim:**
To implement stack operations (push, pop, display) using an array, with messages for stack overflow and stack underflow.

**Algorithm:**
1. Start
2. Define an array `stack` of size MAX and set `top = -1`
3. Display the menu: 1.PUSH 2.POP 3.DISPLAY 4.EXIT
4. Read the choice
5. If choice = 1 (PUSH)
   - If `top == MAX-1`, print "Stack Overflow"
   - Else read the element, increment `top` and store it at `stack[top]`
6. If choice = 2 (POP)
   - If `top == -1`, print "Stack Underflow"
   - Else print `stack[top]` and decrement `top`
7. If choice = 3 (DISPLAY)
   - If `top == -1`, print "Stack is empty"
   - Else print elements from `stack[top]` down to `stack[0]`
8. If choice = 4, stop. Otherwise repeat from step 3.

**Program:**
```c
#include <stdio.h>
#define MAX 3

int stack[MAX];
int top = -1;

void push() {
    int x;
    if (top == MAX - 1) { printf("Stack Overflow\n"); return; }
    printf("Enter element: ");
    scanf("%d", &x);
    stack[++top] = x;
}

void pop() {
    if (top == -1) { printf("Stack Underflow\n"); return; }
    printf("Popped element is %d\n", stack[top--]);
}

void display() {
    if (top == -1) { printf("Stack is empty\n"); return; }
    printf("Top --> ");
    for (int i = top; i >= 0; i--)
        printf("%d ", stack[i]);
    printf("\n");
}

int main() {
    int ch;
    while (1) {
        printf("\n1.PUSH 2.POP 3.DISPLAY 4.EXIT\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1: push(); break;
            case 2: pop(); break;
            case 3: display(); break;
            case 4: return 0;
            default: printf("Invalid choice\n");
        }
    }
}
```

**Output:**
```
1.PUSH 2.POP 3.DISPLAY 4.EXIT
Enter choice: 1
Enter element: 10

Enter choice: 1
Enter element: 20

Enter choice: 1
Enter element: 30

Enter choice: 1
Stack Overflow

Enter choice: 3
Top --> 30 20 10

Enter choice: 2
Popped element is 30

Enter choice: 3
Top --> 20 10

Enter choice: 2
Popped element is 20

Enter choice: 2
Popped element is 10

Enter choice: 2
Stack Underflow

Enter choice: 4
```

**Result:**
Thus the program to implement stack operations using an array was executed and verified successfully.

---

## Ex. No: 1c ARRAY IMPLEMENTATION OF QUEUE

**Aim:**
To implement queue operations (enqueue, dequeue, display) using an array.

**Algorithm:**
1. Start
2. Define an array `queue` of size MAX and set `front = 0`, `rear = -1`
3. Display the menu: 1.ENQUEUE 2.DEQUEUE 3.DISPLAY 4.EXIT
4. Read the choice
5. If choice = 1 (ENQUEUE)
   - If `rear == MAX-1`, print "Queue Full"
   - Else read the element, increment `rear` and store it at `queue[rear]`
6. If choice = 2 (DEQUEUE)
   - If `front > rear`, print "Queue Empty"
   - Else print `queue[front]` and increment `front`
   - If the queue becomes empty, reset `front = 0` and `rear = -1`
7. If choice = 3 (DISPLAY)
   - If `front > rear`, print "Queue is empty"
   - Else print elements from `queue[front]` to `queue[rear]`
8. If choice = 4, stop. Otherwise repeat from step 3.

**Program:**
```c
#include <stdio.h>
#define MAX 3

int queue[MAX];
int front = 0, rear = -1;

void enqueue() {
    int x;
    if (rear == MAX - 1) { printf("Queue Full\n"); return; }
    printf("Enter element: ");
    scanf("%d", &x);
    queue[++rear] = x;
}

void dequeue() {
    if (front > rear) { printf("Queue Empty\n"); return; }
    printf("Deleted element is %d\n", queue[front++]);
    if (front > rear) { front = 0; rear = -1; }
}

void display() {
    if (front > rear) { printf("Queue is empty\n"); return; }
    printf("Front --> ");
    for (int i = front; i <= rear; i++)
        printf("%d ", queue[i]);
    printf("<-- Rear\n");
}

int main() {
    int ch;
    while (1) {
        printf("\n1.ENQUEUE 2.DEQUEUE 3.DISPLAY 4.EXIT\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1: enqueue(); break;
            case 2: dequeue(); break;
            case 3: display(); break;
            case 4: return 0;
            default: printf("Invalid choice\n");
        }
    }
}
```

**Output:**
```
1.ENQUEUE 2.DEQUEUE 3.DISPLAY 4.EXIT
Enter choice: 1
Enter element: 10

Enter choice: 1
Enter element: 20

Enter choice: 1
Enter element: 30

Enter choice: 1
Queue Full

Enter choice: 3
Front --> 10 20 30 <-- Rear

Enter choice: 2
Deleted element is 10

Enter choice: 3
Front --> 20 30 <-- Rear

Enter choice: 2
Deleted element is 20

Enter choice: 2
Deleted element is 30

Enter choice: 2
Queue Empty

Enter choice: 4
```

**Result:**
Thus the program to implement queue operations using an array was executed and verified successfully.

---

## Ex. No: 2 IMPLEMENTATION OF SINGLY LINKED LIST

**Aim:**
To implement a singly linked list and perform insertion, deletion and display operations dynamically.

**Algorithm:**
1. Start
2. Define a node with a data part and a `next` pointer, and set `head = NULL`
3. Display the menu: 1.INSERT 2.DELETE 3.DISPLAY 4.EXIT
4. Read the choice
5. If choice = 1 (INSERT)
   - Create a new node, read its data and set `next = NULL`
   - If `head == NULL`, make the new node the head
   - Else traverse to the last node and link the new node after it
6. If choice = 2 (DELETE)
   - If `head == NULL`, print "List is empty"
   - Read the element to delete and search for it, keeping track of the previous node
   - If not found, print "Element not found"
   - If it is the first node, move `head` to the next node. Else link the previous node to the next node
   - Free the deleted node
7. If choice = 3 (DISPLAY), traverse from `head` until `NULL` and print each element
8. If choice = 4, stop. Otherwise repeat from step 3.

**Program:**
```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *head = NULL;

void insert() {
    struct node *newnode = malloc(sizeof(struct node));
    printf("Enter element: ");
    scanf("%d", &newnode->data);
    newnode->next = NULL;
    if (head == NULL) {
        head = newnode;
        return;
    }
    struct node *temp = head;
    while (temp->next != NULL)
        temp = temp->next;
    temp->next = newnode;
}

void delete() {
    int key;
    if (head == NULL) { printf("List is empty\n"); return; }
    printf("Enter element to delete: ");
    scanf("%d", &key);
    struct node *temp = head, *prev = NULL;
    while (temp != NULL && temp->data != key) {
        prev = temp;
        temp = temp->next;
    }
    if (temp == NULL) { printf("Element not found\n"); return; }
    if (prev == NULL)
        head = temp->next;
    else
        prev->next = temp->next;
    free(temp);
    printf("Deleted %d\n", key);
}

void display() {
    if (head == NULL) { printf("List is empty\n"); return; }
    printf("HEAD -> ");
    for (struct node *temp = head; temp != NULL; temp = temp->next)
        printf("%d -> ", temp->data);
    printf("NULL\n");
}

int main() {
    int ch;
    while (1) {
        printf("\n1.INSERT 2.DELETE 3.DISPLAY 4.EXIT\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1: insert(); break;
            case 2: delete(); break;
            case 3: display(); break;
            case 4: return 0;
            default: printf("Invalid choice\n");
        }
    }
}
```

**Output:**
```
1.INSERT 2.DELETE 3.DISPLAY 4.EXIT
Enter choice: 1
Enter element: 23

Enter choice: 1
Enter element: 45

Enter choice: 1
Enter element: 67

Enter choice: 3
HEAD -> 23 -> 45 -> 67 -> NULL

Enter choice: 2
Enter element to delete: 45
Deleted 45

Enter choice: 3
HEAD -> 23 -> 67 -> NULL

Enter choice: 2
Enter element to delete: 99
Element not found

Enter choice: 2
Enter element to delete: 23
Deleted 23

Enter choice: 3
HEAD -> 67 -> NULL

Enter choice: 4
```

**Result:**
Thus the program to implement a singly linked list was executed and insertion, deletion and display operations were verified successfully.

---
## Ex. No: 4 LINKED LIST IMPLEMENTATION OF LINEAR QUEUE

**Aim:**
To implement queue operations (enqueue, dequeue, display) using a singly linked list.

**Algorithm:**
1. Start
2. Define a node with a data part and a `next` pointer, and set `front = NULL`, `rear = NULL`
3. Display the menu: 1.ENQUEUE 2.DEQUEUE 3.DISPLAY 4.EXIT
4. Read the choice
5. If choice = 1 (ENQUEUE)
   - Create a new node, read its data and set `next = NULL`
   - If `rear == NULL`, make both `front` and `rear` point to the new node
   - Else link the new node after `rear` and move `rear` to it
6. If choice = 2 (DEQUEUE)
   - If `front == NULL`, print "Queue Empty"
   - Else print the data of the `front` node and move `front` to the next node
   - If `front` becomes `NULL`, set `rear = NULL`
   - Free the removed node
7. If choice = 3 (DISPLAY)
   - If `front == NULL`, print "Queue is empty"
   - Else traverse from `front` until `NULL` and print each element
8. If choice = 4, stop. Otherwise repeat from step 3.

**Program:**
```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *next;
};

struct node *front = NULL, *rear = NULL;

void enqueue() {
    struct node *newnode = malloc(sizeof(struct node));
    printf("Enter element: ");
    scanf("%d", &newnode->data);
    newnode->next = NULL;
    if (rear == NULL)
        front = rear = newnode;
    else {
        rear->next = newnode;
        rear = newnode;
    }
}

void dequeue() {
    if (front == NULL) { printf("Queue Empty\n"); return; }
    struct node *temp = front;
    printf("Deleted element is %d\n", temp->data);
    front = front->next;
    if (front == NULL)
        rear = NULL;
    free(temp);
}

void display() {
    if (front == NULL) { printf("Queue is empty\n"); return; }
    printf("Front --> ");
    for (struct node *temp = front; temp != NULL; temp = temp->next)
        printf("%d -> ", temp->data);
    printf("NULL\n");
}

int main() {
    int ch;
    while (1) {
        printf("\n1.ENQUEUE 2.DEQUEUE 3.DISPLAY 4.EXIT\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1: enqueue(); break;
            case 2: dequeue(); break;
            case 3: display(); break;
            case 4: return 0;
            default: printf("Invalid choice\n");
        }
    }
}
```

**Output:**
```
1.ENQUEUE 2.DEQUEUE 3.DISPLAY 4.EXIT
Enter choice: 1
Enter element: 12

Enter choice: 1
Enter element: 23

Enter choice: 1
Enter element: 34

Enter choice: 3
Front --> 12 -> 23 -> 34 -> NULL

Enter choice: 2
Deleted element is 12

Enter choice: 3
Front --> 23 -> 34 -> NULL

Enter choice: 2
Deleted element is 23

Enter choice: 2
Deleted element is 34

Enter choice: 2
Queue Empty

Enter choice: 4
```

**Result:**
Thus the program to implement queue operations using a linked list was executed and verified successfully.

---

#include <stdio.h>

int linearSearch(int a[], int n, int key) {
    for (int i = 0; i < n; i++)
        if (a[i] == key)
            return i;
    return -1;
}

int main() {
    int n, key;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    int a[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    printf("Enter element to search: ");
    scanf("%d", &key);
    int pos = linearSearch(a, n, key);
    if (pos == -1)
        printf("Element %d not found\n", key);
    else
        printf("Element %d found at index %d\n", key, pos);
    return 0;
}

---

## Ex. No: 9a LINEAR SEARCH

**Aim:**
To locate an element in an array using the linear search method.

**Algorithm:**
1. Start
2. Read the number of elements `n` and the array elements
3. Read the element `key` to be searched
4. Set `i = 0`
5. Compare `a[i]` with `key`
   - If they are equal, print "Element found at index i" and stop
6. Increment `i`. If `i < n`, repeat from step 5
7. If the end of the array is reached, print "Element not found"
8. Stop

**Program:**
```c
#include <stdio.h>

int linearSearch(int a[], int n, int key) {
    for (int i = 0; i < n; i++)
        if (a[i] == key)
            return i;
    return -1;
}

int main() {
    int n, key;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    int a[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    printf("Enter element to search: ");
    scanf("%d", &key);
    int pos = linearSearch(a, n, key);
    if (pos == -1)
        printf("Element %d not found\n", key);
    else
        printf("Element %d found at index %d\n", key, pos);
    return 0;
}
```

**Output:**
```
Enter number of elements: 5
Enter 5 elements: 10 25 30 45 60
Enter element to search: 30
Element 30 found at index 2

Enter number of elements: 5
Enter 5 elements: 10 25 30 45 60
Enter element to search: 99
Element 99 not found
```

**Result:**
Thus the program to locate an element in an array using linear search was executed and verified successfully.

---

## Ex. No: 9b BINARY SEARCH

**Aim:**
To locate an element in a sorted array using the binary search method.

**Algorithm:**
1. Start
2. Read the number of elements `n` and the array elements in sorted order
3. Read the element `key` to be searched
4. Set `low = 0` and `high = n - 1`
5. While `low <= high`, repeat steps 6 to 8
6. Find the middle index `mid = (low + high) / 2`
7. If `a[mid] == key`, print "Element found at index mid" and stop
8. Else if `a[mid] < key`, set `low = mid + 1`. Else set `high = mid - 1`
9. If the loop ends, print "Element not found"
10. Stop

**Program:**
```c
#include <stdio.h>

int binarySearch(int a[], int n, int key) {
    int low = 0, high = n - 1;
    while (low <= high) {
        int mid = (low + high) / 2;
        if (a[mid] == key)
            return mid;
        else if (a[mid] < key)
            low = mid + 1;
        else
            high = mid - 1;
    }
    return -1;
}

int main() {
    int n, key;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    int a[n];
    printf("Enter %d elements in sorted order: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    printf("Enter element to search: ");
    scanf("%d", &key);
    int pos = binarySearch(a, n, key);
    if (pos == -1)
        printf("Element %d not found\n", key);
    else
        printf("Element %d found at index %d\n", key, pos);
    return 0;
}
```

**Output:**
```
Enter number of elements: 6
Enter 6 elements in sorted order: 10 20 30 40 50 60
Enter element to search: 40
Element 40 found at index 3

Enter number of elements: 6
Enter 6 elements in sorted order: 10 20 30 40 50 60
Enter element to search: 25
Element 25 not found
```

**Result:**
Thus the program to locate an element in a sorted array using binary search was executed and verified successfully.

---

## Ex. No: 10a INSERTION SORT

**Aim:**
To sort an array of N numbers using insertion sort.

**Algorithm:**
1. Start
2. Read the number of elements `n` and the array elements
3. Repeat steps 4 to 6 for `i = 1` to `n - 1`
4. Set `key = a[i]` and `j = i - 1`
5. While `j >= 0` and `a[j] > key`, move `a[j]` one position right and decrement `j`
6. Place `key` at `a[j + 1]` and display the array after the pass
7. Display the sorted array
8. Stop

**Program:**
```c
#include <stdio.h>

void insertionSort(int a[], int n) {
    for (int i = 1; i < n; i++) {
        int key = a[i], j = i - 1;
        while (j >= 0 && a[j] > key) {
            a[j + 1] = a[j];
            j--;
        }
        a[j + 1] = key;
        printf("After pass %d: ", i);
        for (int k = 0; k < n; k++)
            printf("%d ", a[k]);
        printf("\n");
    }
}

int main() {
    int n;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    int a[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    insertionSort(a, n);
    printf("Sorted array: ");
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
    return 0;
}
```

**Output:**
```
Enter number of elements: 6
Enter 6 elements: 34 8 64 51 32 21
After pass 1: 8 34 64 51 32 21
After pass 2: 8 34 64 51 32 21
After pass 3: 8 34 51 64 32 21
After pass 4: 8 32 34 51 64 21
After pass 5: 8 21 32 34 51 64
Sorted array: 8 21 32 34 51 64
```

**Result:**
Thus the program to sort an array of N numbers using insertion sort was executed and verified successfully.

---

## Ex. No: 10b SELECTION SORT

**Aim:**
To sort an array of N numbers using selection sort.

**Algorithm:**
1. Start
2. Read the number of elements `n` and the array elements
3. Repeat steps 4 to 6 for `i = 0` to `n - 2`
4. Set `min = i`
5. For `j = i + 1` to `n - 1`, if `a[j] < a[min]`, set `min = j`
6. Swap `a[i]` and `a[min]`
7. Display the sorted array
8. Stop

**Program:**
```c
#include <stdio.h>

void selectionSort(int a[], int n) {
    for (int i = 0; i < n - 1; i++) {
        int min = i;
        for (int j = i + 1; j < n; j++)
            if (a[j] < a[min])
                min = j;
        int temp = a[i];
        a[i] = a[min];
        a[min] = temp;
    }
}

int main() {
    int n;
    printf("Enter number of elements: ");
    scanf("%d", &n);
    int a[n];
    printf("Enter %d elements: ", n);
    for (int i = 0; i < n; i++)
        scanf("%d", &a[i]);
    selectionSort(a, n);
    printf("Sorted array: ");
    for (int i = 0; i < n; i++)
        printf("%d ", a[i]);
    printf("\n");
    return 0;
}
```

**Output:**
```
Enter number of elements: 6
Enter 6 elements: 29 10 14 37 13 5
Sorted array: 5 10 13 14 29 37
```

**Result:**
Thus the program to sort an array of N numbers using selection sort was executed and verified successfully.

---

## Ex. No: 7 DIJKSTRA'S ALGORITHM

**Aim:**
To implement Dijkstra's algorithm to find the shortest path from a source node to all other nodes in a graph.

**Algorithm:**
1. Start
2. Read the number of nodes `n`, the adjacency matrix (use 9999 for no edge) and the source node
3. Set `d[i] = 9999` and `vis[i] = 0` for all nodes, then set `d[src] = 0`
4. Repeat steps 5 to 7 for `n - 1` times
5. Pick the unvisited node `u` with the smallest `d`
6. Mark `u` as visited
7. For every unvisited node `i`, if `d[u] + g[u][i] < d[i]`, set `d[i] = d[u] + g[u][i]`
8. Display `d[i]` for all nodes
9. Stop

**Program:**
```c
#include <stdio.h>
#define N 10
#define INF 9999

void dijkstra(int g[N][N], int n, int src) {
    int d[N], vis[N] = {0};
    for (int i = 0; i < n; i++)
        d[i] = INF;
    d[src] = 0;
    for (int r = 0; r < n - 1; r++) {
        int u = -1;                  // pick unvisited node with min d
        for (int i = 0; i < n; i++)
            if (!vis[i] && (u == -1 || d[i] < d[u]))
                u = i;
        vis[u] = 1;
        for (int i = 0; i < n; i++)  // relax
            if (!vis[i] && d[u] + g[u][i] < d[i])
                d[i] = d[u] + g[u][i];
    }
    printf("Shortest distances from node %d:\n", src);
    for (int i = 0; i < n; i++)
        printf("To node %d: %d\n", i, d[i]);
}

int main() {
    int g[N][N], n, src;
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    printf("Enter adjacency matrix (9999 for no edge):\n");
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            scanf("%d", &g[i][j]);
    printf("Enter source node: ");
    scanf("%d", &src);
    dijkstra(g, n, src);
    return 0;
}
```

**Output:**
```
Enter number of nodes: 5
Enter adjacency matrix (9999 for no edge):
0 10 9999 30 100
10 0 50 9999 9999
9999 50 0 20 10
30 9999 20 0 60
100 9999 10 60 0
Enter source node: 0
Shortest distances from node 0:
To node 0: 0
To node 1: 10
To node 2: 50
To node 3: 30
To node 4: 60
```

**Result:**
Thus the program to find the shortest paths using Dijkstra's algorithm was executed and verified successfully.

---

## Ex. No: 8 PRIM'S ALGORITHM

**Aim:**
To find the minimum spanning tree of a weighted graph using Prim's algorithm.

**Algorithm:**
1. Start
2. Read the number of nodes `n` and the adjacency matrix (use 9999 for no edge)
3. Set `vis[i] = 0` for all nodes, then mark node 0 as visited and set `total = 0`
4. Repeat steps 5 to 7 for `n - 1` times
5. Among all edges `(i, j)` where `i` is visited and `j` is not visited, find the edge with the minimum cost
6. Print that edge and add its cost to `total`
7. Mark `j` as visited
8. Print `total`
9. Stop

**Program:**
```c
#include <stdio.h>
#define N 10
#define INF 9999

int main() {
    int g[N][N], n, vis[N] = {0}, total = 0;
    printf("Enter number of nodes: ");
    scanf("%d", &n);
    printf("Enter adjacency matrix (9999 for no edge):\n");
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            scanf("%d", &g[i][j]);

    vis[0] = 1;
    for (int e = 0; e < n - 1; e++) {
        int min = INF, a = -1, b = -1;
        for (int i = 0; i < n; i++)       // i = visited node
            for (int j = 0; j < n; j++)   // j = unvisited node
                if (vis[i] && !vis[j] && g[i][j] < min) {
                    min = g[i][j];
                    a = i;
                    b = j;
                }
        printf("Edge %d - %d  cost %d\n", a, b, min);
        vis[b] = 1;
        total += min;
    }
    printf("Total cost of minimum spanning tree = %d\n", total);
    return 0;
}
```

**Output:**
```
Enter number of nodes: 5
Enter adjacency matrix (9999 for no edge):
0 2 9999 6 9999
2 0 3 8 5
9999 3 0 9999 7
6 8 9999 0 9
9999 5 7 9 0
Edge 0 - 1  cost 2
Edge 1 - 2  cost 3
Edge 1 - 4  cost 5
Edge 0 - 3  cost 6
Total cost of minimum spanning tree = 16
```

**Result:**
Thus the program to find the minimum spanning tree using Prim's algorithm was executed and verified successfully.

---

## Ex. No: 5 POLYNOMIAL ADDITION AND MULTIPLICATION USING LINKED LIST

**Aim:**
To represent polynomials using linked lists and perform addition and multiplication of two polynomials.

**Algorithm:**
1. Start
2. Define a node with `coef`, `power` and a `next` pointer
3. Define `insert(coef, power)`, which places a term in a list kept in descending order of power
   - If a term with the same power already exists, add the coefficients
   - Else create a new node and link it at the correct position
4. Read the number of terms and the (coefficient, power) pairs of polynomial 1 and polynomial 2, using `insert`
5. ADDITION: create an empty result list, insert every term of polynomial 1, then every term of polynomial 2
6. MULTIPLICATION: create an empty result list. For every term `p` of polynomial 1 and every term `q` of polynomial 2, insert (`p.coef * q.coef`, `p.power + q.power`)
7. Display polynomial 1, polynomial 2, the sum and the product
8. Stop

**Program:**
```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int coef, power;
    struct node *next;
};

void insert(struct node **head, int coef, int power) {
    struct node *cur = *head, *prev = NULL;
    while (cur != NULL && cur->power > power) {
        prev = cur;
        cur = cur->next;
    }
    if (cur != NULL && cur->power == power) {   // same power: add coefficients
        cur->coef += coef;
        return;
    }
    struct node *t = malloc(sizeof(struct node));
    t->coef = coef;
    t->power = power;
    t->next = cur;
    if (prev == NULL)
        *head = t;
    else
        prev->next = t;
}

struct node *read() {
    struct node *head = NULL;
    int n, c, p;
    printf("Enter number of terms: ");
    scanf("%d", &n);
    printf("Enter coefficient and power of each term:\n");
    for (int i = 0; i < n; i++) {
        scanf("%d %d", &c, &p);
        insert(&head, c, p);
    }
    return head;
}

void display(struct node *h) {
    for (; h != NULL; h = h->next) {
        printf("%dx^%d", h->coef, h->power);
        if (h->next != NULL)
            printf(" + ");
    }
    printf("\n");
}

struct node *add(struct node *a, struct node *b) {
    struct node *r = NULL;
    for (; a != NULL; a = a->next)
        insert(&r, a->coef, a->power);
    for (; b != NULL; b = b->next)
        insert(&r, b->coef, b->power);
    return r;
}

struct node *multiply(struct node *a, struct node *b) {
    struct node *r = NULL;
    for (struct node *p = a; p != NULL; p = p->next)
        for (struct node *q = b; q != NULL; q = q->next)
            insert(&r, p->coef * q->coef, p->power + q->power);
    return r;
}

int main() {
    printf("Polynomial 1\n");
    struct node *p1 = read();
    printf("Polynomial 2\n");
    struct node *p2 = read();
    printf("\nPolynomial 1: ");
    display(p1);
    printf("Polynomial 2: ");
    display(p2);
    printf("Sum:          ");
    display(add(p1, p2));
    printf("Product:      ");
    display(multiply(p1, p2));
    return 0;
}
```

**Output:**
```
Polynomial 1
Enter number of terms: 3
Enter coefficient and power of each term:
3 2
2 1
1 0
Polynomial 2
Enter number of terms: 2
Enter coefficient and power of each term:
2 1
4 0

Polynomial 1: 3x^2 + 2x^1 + 1x^0
Polynomial 2: 2x^1 + 4x^0
Sum:          3x^2 + 4x^1 + 5x^0
Product:      6x^3 + 16x^2 + 10x^1 + 4x^0
```

**Result:**
Thus the program to add and multiply two polynomials using linked lists was executed and verified successfully.

---



---

## Ex. No: 6 BINARY SEARCH TREE

**Aim:**
To construct a binary search tree and perform insertion, deletion, searching, finding the minimum and maximum, and traversals.

**Algorithm:**
1. Start
2. Define a node with `data`, `left` and `right` pointers, and set `root = NULL`
3. Display the menu and read the choice
4. INSERT: if the tree is empty, create the node. Else go left if `x < data`, go right if `x > data`, and insert at the empty position
5. DELETE: search for the node
   - Leaf: remove it
   - One child: replace the node with its child
   - Two children: copy the minimum value of the right subtree into the node, then delete that minimum from the right subtree
6. SEARCH: from the root, go left if `x < data`, right if `x > data`, until found or `NULL`
7. MIN: keep going left until there is no left child. MAX: keep going right until there is no right child
8. INORDER (left, root, right), PREORDER (root, left, right), POSTORDER (left, right, root)
9. If choice = 9, stop. Otherwise repeat from step 3.

**Program:**
```c
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *left, *right;
};

struct node *root = NULL;

struct node *insert(struct node *t, int x) {
    if (t == NULL) {
        t = malloc(sizeof(struct node));
        t->data = x;
        t->left = t->right = NULL;
    } else if (x < t->data)
        t->left = insert(t->left, x);
    else if (x > t->data)
        t->right = insert(t->right, x);
    else
        printf("Duplicate element\n");
    return t;
}

struct node *findmin(struct node *t) {
    while (t != NULL && t->left != NULL)
        t = t->left;
    return t;
}

struct node *findmax(struct node *t) {
    while (t != NULL && t->right != NULL)
        t = t->right;
    return t;
}

struct node *delete(struct node *t, int x) {
    if (t == NULL) {
        printf("Element not found\n");
        return NULL;
    }
    if (x < t->data)
        t->left = delete(t->left, x);
    else if (x > t->data)
        t->right = delete(t->right, x);
    else if (t->left != NULL && t->right != NULL) {   // two children
        t->data = findmin(t->right)->data;
        t->right = delete(t->right, t->data);
    } else {                                          // zero or one child
        struct node *temp = t;
        t = (t->left != NULL) ? t->left : t->right;
        free(temp);
    }
    return t;
}

struct node *search(struct node *t, int x) {
    if (t == NULL || t->data == x)
        return t;
    if (x < t->data)
        return search(t->left, x);
    return search(t->right, x);
}

void inorder(struct node *t) {
    if (t == NULL) return;
    inorder(t->left);
    printf("%d ", t->data);
    inorder(t->right);
}

void preorder(struct node *t) {
    if (t == NULL) return;
    printf("%d ", t->data);
    preorder(t->left);
    preorder(t->right);
}

void postorder(struct node *t) {
    if (t == NULL) return;
    postorder(t->left);
    postorder(t->right);
    printf("%d ", t->data);
}

int main() {
    int ch, x;
    struct node *temp;
    while (1) {
        printf("\n1.INSERT 2.DELETE 3.SEARCH 4.MIN 5.MAX 6.INORDER 7.PREORDER 8.POSTORDER 9.EXIT\nEnter choice: ");
        scanf("%d", &ch);
        switch (ch) {
            case 1:
                printf("Enter element: ");
                scanf("%d", &x);
                root = insert(root, x);
                break;
            case 2:
                printf("Enter element to delete: ");
                scanf("%d", &x);
                root = delete(root, x);
                break;
            case 3:
                printf("Enter element to search: ");
                scanf("%d", &x);
                if (search(root, x) != NULL)
                    printf("Element found\n");
                else
                    printf("Element not found\n");
                break;
            case 4:
                temp = findmin(root);
                if (temp == NULL) printf("Tree is empty\n");
                else printf("Minimum element: %d\n", temp->data);
                break;
            case 5:
                temp = findmax(root);
                if (temp == NULL) printf("Tree is empty\n");
                else printf("Maximum element: %d\n", temp->data);
                break;
            case 6: printf("Inorder: ");   inorder(root);   printf("\n"); break;
            case 7: printf("Preorder: ");  preorder(root);  printf("\n"); break;
            case 8: printf("Postorder: "); postorder(root); printf("\n"); break;
            case 9: return 0;
            default: printf("Invalid choice\n");
        }
    }
}
```

**Output:**
```
1.INSERT 2.DELETE 3.SEARCH 4.MIN 5.MAX 6.INORDER 7.PREORDER 8.POSTORDER 9.EXIT
(insert 50, 30, 70, 20, 40, 60, 80, one at a time with choice 1)

Enter choice: 6
Inorder: 20 30 40 50 60 70 80

Enter choice: 7
Preorder: 50 30 20 40 70 60 80

Enter choice: 8
Postorder: 20 40 30 60 80 70 50

Enter choice: 4
Minimum element: 20

Enter choice: 5
Maximum element: 80

Enter choice: 3
Enter element to search: 60
Element found

Enter choice: 3
Enter element to search: 90
Element not found

Enter choice: 2
Enter element to delete: 20

Enter choice: 2
Enter element to delete: 30

Enter choice: 2
Enter element to delete: 50

Enter choice: 6
Inorder: 40 60 70 80

Enter choice: 7
Preorder: 60 40 70 80

Enter choice: 9
```

**Result:**
Thus the program to implement a binary search tree was executed and insertion, deletion, searching and traversal operations were verified successfully.

---
