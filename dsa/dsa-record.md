PERI Institute of Technology
(Autonomous)
Department of Information Technology
VISION AND MISSION OF THE INSTITUTION
Vision
PERI Institute of Technology visualizes growing in future to an internationally recognized
seat of higher learning in engineering, technology & science. It also visualizes being a research
incubator for academicians, industrialists and researchers from across the world, enabling them to
work in an environment with the sophisticated and state of the art equipment and amenities provided
at the institute.
Mission
In the process of realization of its Vision, PERIIT strives to provide quality technical
education at affordable cost in a challenging & stimulating environment with state-of-the-art facilities
and a global team of dedicated and talented academicians, without compromising in its core values of
honesty, transparency and excellence.
VISION AND MISSION OF THE DEPARTMENT
About the Department
The Information Technology department was established, during the Academic Year 2023-
2024, with an intake of 60 students. Department Objective: We, Department of IT aspire to establish
a system of Quality Assurance, which would on a continuous basis, evaluate and monitor the quality
of education and training imparted at the Institute; improve the teaching-learning process and
ultimately, develop the Department of Information Technology as a Centre of Excellence.
Vision
To provide reliable and modern technology resources to the faculty and students to develop
the competence in Information Technology and to endure with the rapidly changing world to serve
the mankind.
Mission
 Imparting technical knowledge through innovative teaching and research for budding
professionals.
 To equip the students with strong fundamentals, programming and problem solving
skills with an exposure to emerging technologies and inculcate leadership qualities with
a passion to serve society.
 To promote research-based projects / activities in the emerging areas of technology.

24AD303 DATA STRUCTURE & ALGORITHMS
LIST OF EXERCISES
1. Array implementation of List, Stack and Queue ADTs.
2. Implementation of Singly Linked List.
3. Write a program to simulate the working of stack using an array with the following:
i) Push ii) Pop iii) Display The program should print appropriate messages for stack
overflow, stack underflow.
4. Linked list implementation of Linear Queue ADTs .
5. Implementation of Polynomial addition and multiplication using Linked list.
6. Implementation of Binary Search Trees.
7. Implementation of Dijkstra’s Algorithm.
8. Implementation of Prim’s Algorithm.
9. Implementation of Linear Search and Binary Search.
10. Implementation of Insertion Sort and Selection Sort
TOTAL PERIODS: 30 PERIODS

INDEX

|     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- |

|     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- |
Page  Marks
| S.no  | DATE  |     | Name of the Program  |     |     |     | Sign  |
| ----- | ----- | --- | -------------------- | --- | --- | --- | ----- |
no  Obtained
| 1    |     | Array implementation of List, Stack and Queue   |     |     |     |     |     |
| ---- | --- | ----------------------------------------------- | --- | --- | --- | --- | --- |
ADTs.

| 2    |     |     |     |     |     |     |     |
| ---- | --- | --- | --- | --- | --- | --- | --- |
Implementation of Singly Linked List.

| 3    |     |     |     |     |     |     |     |
| ---- | --- | --- | --- | --- | --- | --- | --- |
Write a program to simulate the working of stack
using an array with the following:
i) Push ii) Pop iii) Display The program
|     |     | should  print  | appropriate  | messages  | for  |     |     |
| --- | --- | -------------- | ------------ | --------- | ---- | --- | --- |
stack overflow, stack underflow.

| 4    |     | Linked list implementation of Linear Queue  |     |     |     |     |     |
| ---- | --- | ------------------------------------------- | --- | --- | --- | --- | --- |
ADTs
| 5    |     |     |     |     |     |     |     |
| ---- | --- | --- | --- | --- | --- | --- | --- |
Implementation of Polynomial addition and
multiplication using Linked list.
| 6    |     |     |     |     |     |     |     |
| ---- | --- | --- | --- | --- | --- | --- | --- |
Implementation of Binary Search Trees.

| 7    |     |     |     |     |     |     |     |
| ---- | --- | --- | --- | --- | --- | --- | --- |
Implementation of Dijkstra’s Algorithm.

| 8    |     |     |     |     |     |     |     |
| ---- | --- | --- | --- | --- | --- | --- | --- |
Implementation of Prim’s Algorithm.

| 9    |     |     |     |     |     |     |     |
| ---- | --- | --- | --- | --- | --- | --- | --- |
Implementation of Linear Search and Binary
Search.

| 10    |     |     |     |     |     |     |     |
| ----- | --- | --- | --- | --- | --- | --- | --- |
Implementation of Insertion Sort and Selection
Sort

Ex. No:1a ARRAY IMPLEMENTATION OF LIST
Date:
Aim:
To create a list using array and perform operations such as display, insertions and deletions.
Algorithm
1. Start
2. Define list using an array of size n.
3. First item with subscript or position = 0
4. Display menu on list operation
5. Accept user choice
6. If choice = 1 then
7. Locate node after which insertion is to be done
8. Create an empty location in array after the node by moving the existing elements one
position ahead.
9. Insert the new element at appropriate position
10. Else if choice = 2
11. Get element to be deleted.
12. Locate the position of the element replace the element with the element in the
following position.
13. Repeat the step for successive elements until end of the array.
14. Else
15. Traverse the list from position or subscript 0 to n.
16. Stop
PROGRAM
#include<stdio.h>
#include<conio.h>
#define MAX 10
void create();
void insert();
void deletion();
void search();
void display();
int a,b[20], n, p, e, f, i, pos;
void main()
{
//clrscr();
int ch;
char g='y';
do
{

printf("\n main Menu");
printf("\n 1.Create \n 2.Delete \n 3.Search \n 4.Insert \n 5.Display\n 6.Exit
\n");
printf("\n Enter your Choice");
scanf("%d", &ch);
switch(ch)
{
case 1:
create();
break;
case 2:
deletion();
break;
case 3:
search();
break;
case 4:
insert();
break;
case 5:
display();
break;
case 6:
exit();
break;
default:
printf("\n Enter the correct choice:");
}
printf("\n Do u want to continue:::");
scanf("\n%c", &g);
}
while(g=='y'||g=='Y');
getch();
}
void create()
{
printf("\n Enter the number of nodes");
scanf("%d", &n);
for(i=0;i<n;i++)
{
printf("\n Enter the Element:",i+1);
scanf("%d", &b[i]);
}
}
void deletion()
{

printf("\n Enter the position u want to delete::");
scanf("%d", &pos);
if(pos>=n)
{
printf("\n Invalid Location::");
}
else
{
for(i=pos+1;i<n;i++)
{
b[i-1]=b[i];
}
n--;
}
printf("\n The Elements after deletion");
for(i=0;i<n;i++)
{
printf("\t%d", b[i]);
}
}
void search()
{
printf("\n Enter the Element to be searched:");
scanf("%d", &e);
for(i=0;i<n;i++)
{
if(b[i]==e)
{
printf("Value is in the %d Position", i);
}
else
{
printf("Value %d is not in the list::", e);
continue;
}
}
}
void insert()
{
printf("\n Enter the position u need to insert::");
scanf("%d", &pos);
if(pos>=n)
{
printf("\n invalid Location::");
}

else
{
for(i=MAX-1;i>=pos-1;i--)
{
b[i+1]=b[i];
}
printf("\n Enter the element to insert::\n");
scanf("%d",&p);
b[pos]=p;
n++;
}
printf("\n The list after insertion::\n");
display();
}
void display()
{
printf("\n The Elements of The list ADT are:");
for(i=0;i<n;i++)
{
printf("\n\n%d", b[i]);
}
}
Output
Array of 10 numbers:
Input elements:
1
2
4
5
6
7
8
9
10
11
Current array: 1 2 4 5 6 7 8 9 10 11
Would you like to enter another element? [1/0]: 1 Input
element: 3
Input position: 2
Current array: 1 2 3 4 5 6 7 8 9 10
Result:
Thus the above program of list using array is created and operations such as display, insertions
and deletions are performed and verified successfully.

Ex. No:1b ARRAY IMPLEMENTATION OF STACK
Date:
Aim: To implement stack operations using array.
Algorithm
1. Start
2. Define a array stack of size max = 5
3. Initialize top = -1
4. Display a menu listing stack operations
5. Accept choice
6. If choice = 1 then
7. If top < max -1
8. Increment top
9. Store element at current position of top
10. Else
11. Print Stack overflow
12. If choice = 2 then
13. If top < 0 then
14. Print Stack underflow
15. Else
16. Display current top element
17. Decrement top
18. If choice = 3 then
19. Display stack elements starting from top
20. Stop
Program
/* 1a - Stack Operation using Arrays */
#include <stdio.h>
#include <conio.h>
#define max 5
static int stack[max];
int top = -1;
void push(int x)
{
stack[++top] = x;
}
int pop()
{
return (stack[top--]);
}
void view()
{
int i;
if (top < 0)
printf("\n Stack Empty \n");
else
{
printf("\n Top-->");

for(i=top; {
i>=0; i--)
printf("%4d", stack[i]);
}
printf("\n");
}
}
main()
{
int ch=0, val;
clrscr();
while(ch != 4)
{
printf("\n STACK OPERATION \n");
printf("1.PUSH ");
printf("2.POP ");
printf("3.VIEW ");
printf("4.QUIT \n");
printf("Enter Choice : ");
scanf("%d", &ch);
switch(ch)
{
case 1:
if(top < max-1)
{
printf("\nEnter Stack element : ");
scanf("%d", &val);
push(val);
}
else
printf("\n Stack Overflow \n");
break;
case 2:
if(top < 0)
printf("\n Stack Underflow \n");
else
{
val = pop();
printf("\n Popped element is %d\n", val);
}
break;
case 3:
view();
break;
case 4:

exit(0);
default:
printf("\n Invalid Choice \n");
}
}
}
Output
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 1
Enter Stack element : 12
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 1
Enter Stack element : 23
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 1
Enter Stack element : 34
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 1
Enter Stack element : 45
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 3
Top--> 45 34 23 12
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 2
Popped element is 45
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 3
Top--> 34 23 12
STACK OPERATION
1.PUSH 2.POP 3.VIEW 4.QUIT
Enter Choice : 4
Result:
Thus the above program of stack operations using array are implemented and
verified successfully.

Ex. No:1c ARRAY IMPLEMENTATION OF QUEUE
Date:
Aim: To implement queue operations using array.
Algorithm
1. Start
2. Define a array queue of size max = 5
3. Initialize front = rear = –1
4. Display a menu listing queue operations
5. Accept choice
6. If choice = 1 then
7. If rear < max -1
8. Increment rear
9. Store element at current position of rear
10. Else
11. Print Queue Full
12. If choice = 2 then
13. If front = –1 then
14. Print Queue empty
15. Else
16. Display current front element
17. Increment front
18. If choice = 3 then
19. Display queue elements starting from front to rear.
20. Stop
Program
/* 1b - Queue Operation using Arrays */
#include <stdio.h>
#include <conio.h>
#define max 5
static int queue[max];
int front = -1;
int rear = -1;
void insert(int x)
{
queue[++rear] = x;
if (front == -1)
front = 0;
}
int remove()
{
int val;
val = queue[front];
if (front==rear && rear==max-1)
front = rear = -1;
else
front ++;
return (val);

}
void view()
{
int i;
if (front == -1)
printf("\n Queue Empty \n");
else
{
printf("\n Front-->");
for(i=front; i<=rear; i++)
printf("%4d", queue[i]);
printf(" <--Rear\n");
}
}
main()
{
int ch= 0,val;
clrscr();
while(ch != 4)
{
printf("\n QUEUE OPERATION \n");
printf("1.INSERT ");
printf("2.DELETE ");
printf("3.VIEW ");
printf("4.QUIT\n");
printf("Enter Choice : ");
scanf("%d", &ch);
switch(ch)
{
case 1:
if(rear < max-1)
{
printf("\n Enter element to be inserted : ");
scanf("%d", &val);
insert(val);
}
else
printf("\n Queue Full \n");
break;
case 2:
if(front == -1)
printf("\n Queue Empty \n");
else

{
val = remove();
printf("\n Element deleted : %d \n", val);
}
break;
case 3:
view();
break;
case 4:
exit(0);
default:
printf("\n Invalid Choice \n");
}
}
}
Output
QUEUE OPERATION
1.INSERT 2.DELETE 3.VIEW 4.QUIT
Enter Choice : 1
Enter element to be inserted : 12
QUEUE OPERATION
1.INSERT 2.DELETE 3.VIEW 4.QUIT
Enter Choice : 1
Enter element to be inserted : 23
QUEUE OPERATION
1.INSERT 2.DELETE 3.VIEW 4.QUIT
Enter Choice : 1
Enter element to be inserted : 34
QUEUE OPERATION
1.INSERT 2.DELETE 3.VIEW 4.QUIT
Enter Choice : 1
Enter element to be inserted : 45
QUEUE OPERATION
1.INSERT 2.DELETE 3.VIEW 4.QUIT
Enter Choice : 1
Enter element to be inserted : 56
QUEUE OPERATION
1.INSERT 2.DELETE 3.VIEW 4.QUIT
Enter Choice : 1 Queue Full
QUEUE OPERATION
1.INSERT 2.DELETE 3.VIEW 4.QUIT
Enter Choice : 3
Front--> 12 23 34 45 56 <--Rear
Result:
Thus the above program of Queue operations using array are implemented and
verified successfully.

Ex. No:2 LINKED LIST IMPLEMENTATION OF LIST [SINGLY LINKED LIST]
Date:
Aim:
To define a singly linked list node and perform operations such as insertions and deletions dynamically.
Algorithm
1. Start
2. Define single linked list node as self referential structure
3. Create Head node with label = -1 and next = NULL using
4. Display menu on list operation
5. Accept user choice
6. If choice = 1 then
7. Locate node after which insertion is to be done
8. Create a new node and get data part
9. Insert the new node at appropriate position by manipulating address
10. Else if choice = 2
11. Get node's data to be deleted.
12. Locate the node and delink the node
13. Rearrange the links
14. Else
15. Traverse the list from Head node to node which points to null
16. Stop
Program
/* 3c - Single Linked List */
#include <stdio.h>
#include <conio.h>
#include <process.h>
#include <alloc.h>
#include <string.h>
struct node
{
int label;
struct node *next;
};
main()
{
int ch, fou=0;
int k;
struct node *h, *temp, *head, *h1;
/* Head node construction */
head = (struct node*) malloc(sizeof(struct node));
head->label = -1;
head->next = NULL;
while(-1)
{
clrscr();

printf("\n\n SINGLY LINKED LIST OPERATIONS \n");
printf("1->Add ");
printf("2->Delete ");
printf("3->View ");
printf("4->Exit \n");
printf("Enter your choice : ");
scanf("%d", &ch);
switch(ch)
{
/* Add a node at any intermediate location */
case 1:
printf("\n Enter label after which to add : ");
scanf("%d", &k);
h = head;
fou = 0;
if (h->label == k)
fou = 1;
while(h->next != NULL)
{
if (h->label == k)
{
fou=1;
break;
}
h = h->next;
}
if (h->label == k)
fou = 1;
if (fou != 1)
printf("Node not found\n");
else
{
temp=(struct node *)(malloc(sizeof(struct node)));
printf("Enter label for new node : ");
scanf("%d" , &temp->label);
temp->next = h->next;
h->next = temp;
}
break;
/* Delete any intermediate node */
case 2:
printf("Enter label of node to be deleted\n");
scanf("%d", &k);
fou = 0;
h = h1 = head;
while (h->next != NULL)
{
h = h->next;
if (h->label == k)

{
fou = 1;
break;
}
}
if (fou == 0)
printf("Sorry Node not found\n");
else
{
while (h1->next != h)
h1 = h1->next;
h1->next = h->next;
free(h);
printf("Node deleted successfully \n");
}
break;
case 3:
printf("\n\n HEAD -> ");
h=head;
while (h->next != NULL)
{
h = h->next;
printf("%d -> ",h->label);
}
printf("NULL"); break;
case 4: exit(0);
}
}
}

Output
SINGLY LINKED LIST OPERATIONS
1->Add 2->Delete 3->View 4->Exit
Enter your choice : 1
Enter label after which new node is to be added : -1
Enter label for new node : 23
SINGLY LINKED LIST OPERATIONS
1->Add 2->Delete 3->View 4->Exit
Enter your choice : 1
Enter label after which new node is to be added : 23
Enter label for new node : 67
SINGLY LINKED LIST OPERATIONS
1->Add 2->Delete 3->View 4->Exit
Enter your choice : 3
HEAD -> 23 -> 67 -> NULL
Result:
Thus the above program a singly linked list node is created and operations such as display,
insertions and deletions are performed and verified successfully.

Ex. No:3 LINKED LIST IMPLEMENTATION OF ARRAY
Date:
Aim:
To implement stack operations using linked list.
Algorithm
1. Start
2. Define a singly linked list node for stack
3. Create Head node
4. Display a menu listing stack operations
5. Accept choice
6. If choice = 1 then
7. Create a new node with data
8. Make new node point to first node
9. Make head node point to new node
10. If choice = 2 then
11. Make temp node point to first node
12. Make head node point to next of temp node
13. Release memory
14. If choice = 3 then
15. Display stack elements starting from head node till null
16. Stop
Program
/* 5c - Stack using Single Linked List */
#include <stdio.h>
#include <conio.h>
#include <process.h>
#include <alloc.h>
struct node
{
int label;
struct node *next;
};
main()
{
int ch = 0;
int k;
struct node *h, *temp, *head;
/* Head node construction */
head = (struct node*) malloc(sizeof(struct node));
head->next = NULL;
while(1)
{
printf("\n Stack using Linked List \n");
printf("1->Push ");

printf("2->Pop ");
printf("3->View ");
printf("4->Exit \n");
printf("Enter your choice : ");
scanf("%d", &ch);
switch(ch)
{
case 1:
/* Create a new node */
temp=(struct node *)(malloc(sizeof(struct node)));
printf("Enter label for new node : ");
scanf("%d", &temp->label);
h = head;
temp->next = h->next;
h->next = temp;
break;
case 2:
/* Delink the first node */
h = head->next;
head->next = h->next;
printf("Node %s deleted\n", h->label);
free(h);
break;
case 3:
printf("\n HEAD -> ");
h = head;
/* Loop till last node */
while(h->next != NULL)
{
h = h->next;
printf("%d -> ",h->label);
}
printf("NULL \n");
break;
case 4:
exit(0);
}
}
}
Output
Stack using Linked List
1->Push 2->Pop 3->View 4->Exit
Enter your choice : 1
Enter label for new node : 23
New node added
Stack using Linked List
1->Push 2->Pop 3->View 4->Exit

Enter your choice : 1
Enter label for new node : 34
Stack using Linked List
1->Push 2->Pop 3->View 4->Exit
Enter your choice : 3
HEAD -> 34 -> 23 -> NULL
Result:
Thus the above program of stack operations using linked list are implemented and
verified successfully.

Ex. No:4 LINKED LIST IMPLEMENTATION OF QUEUE
Date:
Aim:
To implement queue operations using linked list.
Algorithm
1. Start
2. Define a singly linked list node for stack
3. Create Head node
4. Display a menu listing stack operations
5. Accept choice
6. If choice = 1 then
7. Create a new node with data
8. Make new node point to first node
9. Make head node point to new node
10. If choice = 2 then
11. Make temp node point to first node
12. Make head node point to next of temp node
13. Release memory
14. If choice = 3 then
15. Display stack elements starting from head node till null
16. Stop
Program
/* 3c - Queue using Single Linked List */
#include <stdio.h>
#include <conio.h>
#include <process.h>
#include <alloc.h>
struct node
{
int label;
struct node *next;
};
main()
{
int ch=0;
int k;
struct node *h, *temp, *head;
/* Head node construction */
head = (struct node*) malloc(sizeof(struct node));
head->next = NULL;
while(1)
{
printf("\n Queue using Linked List \n");
printf("1->Insert ");
printf("2->Delete ");
printf("3->View ");

printf("4->Exit \n");
printf("Enter your choice : ");
scanf("%d", &ch);
switch(ch)
{
case 1:
/* Create a new node */
temp=(struct node *)(malloc(sizeof(struct node)));
printf("Enter label for new node : ");
scanf("%d", &temp->label);
/* Reorganize the links */
h = head;
while (h->next != NULL)
h = h->next;
h->next = temp;
temp->next = NULL;
break;
case 2:
/* Delink the first node */
h = head->next;
head->next = h->next;
printf("Node deleted \n");
free(h);
break;
case 3:
printf("\n\nHEAD -> ");
h=head;
while (h->next!=NULL)
{
h = h->next;
printf("%d -> ",h->label);
}
printf("NULL \n");
break;
case 4:
exit(0);
}
}
}

Output
Queue using Linked List
1->Insert 2->Delete 3->View 4->Exit
Enter your choice : 1
Enter label for new node : 12
Queue using Linked List
1->Insert 2->Delete 3->View 4->Exit
Enter your choice : 1
Enter label for new node : 23
Queue using Linked List
1->Insert 2->Delete 3->View 4->Exit
Enter your choice : 3
HEAD -> 12 -> 23 -> NULL
Result:.
Thus the above program of Queue operations using linked list are implemented and
verified successfully.

Ex. No:5 APPLICATIONS OF LIST POLYNOMIAL ADDITION AND SUBTRACTION
Date:
Aim:
To store a polynomial using linked list. Also, perform addition and subtraction on two polynomials.
Algorithm
Let p and q be the two polynomials represented by linked lists
1. while p and q are not null, repeat step 2.
2. If powers of the two terms are equal then
If the terms do not cancel then
Insert the sum of the terms into the sum Polynomial
Advance p Advance q
Else if the power of the first polynomial> power of second Then
Insert the term from first polynomial into sum polynomial
Advance p
Else
insert the term from second polynomial into sum polynomial Advance q
3. Copy the remaining terms from the non empty polynomial into the sum polynomial.
The third step of the algorithm is to be processed till the end of the polynomials has not been
reached.
Program
#include <stdio.h>#include <stdlib.h>
struct Node
{
int coeff;
int power;
struct Node *next;
};
struct Node* createNode(int coeff, int power)
{
struct Node *newNode = (struct Node*)malloc(sizeof(struct Node));
newNode->coeff = coeff;
newNode->power = power;
newNode->next = NULL;
return newNode;
}
void insert(struct Node **head, int coeff, int power)
{
struct Node *newNode = createNode(coeff, power);
if (*head == NULL)
{
*head = newNode;
return;
}

struct Node *temp = *head;
while (temp->next != NULL)
temp = temp->next;
temp->next = newNode;
}
struct Node* add(struct Node *p1, struct Node *p2)
{
struct Node *result = NULL;
while (p1 != NULL && p2 != NULL)
{
if (p1->power == p2->power)
{
insert(&result, p1->coeff + p2->coeff, p1->power);
p1 = p1->next;
p2 = p2->next;
}
else if (p1->power > p2->power) {
insert(&result, p1->coeff, p1->power);
p1 = p1->next;
}
else {
insert(&result, p2->coeff, p2->power);
p2 = p2->next;
}
}
while (p1 != NULL) {
insert(&result, p1->coeff, p1->power);
p1 = p1->next;
}
while (p2 != NULL) {
insert(&result, p2->coeff, p2->power);
p2 = p2->next;
}
return result;
}
struct Node* subtract(struct Node *p1, struct Node *p2)
{
struct Node *result = NULL;
while (p1 != NULL && p2 != NULL) {
if (p1->power == p2->power) {
insert(&result, p1->coeff - p2->coeff, p1->power);

p1 = p1->next;
p2 = p2->next;
}
else if (p1->power > p2->power) {
insert(&result, p1->coeff, p1->power);
p1 = p1->next;
}
else {
insert(&result, -p2->coeff, p2->power);
p2 = p2->next;
}
}
while (p1 != NULL) {
insert(&result, p1->coeff, p1->power);
p1 = p1->next;
}
while (p2 != NULL) {
insert(&result, -p2->coeff, p2->power);
p2 = p2->next;
}
return result;
}
void display(struct Node *head) {
while (head != NULL) {
printf("%dx^%d", head->coeff, head->power);
head = head->next;
if (head != NULL)
printf(" + ");
}
printf("\n");
}
int main() {
struct Node *p1 = NULL, *p2 = NULL;
struct Node *sum, *diff;
// Polynomial 1: 5x^2 + 4x^1 + 2
insert(&p1, 5, 2);
insert(&p1, 4, 1);
insert(&p1, 2, 0);
// Polynomial 2: 3x^2 + 2x^1 + 1
insert(&p2, 3, 2);
insert(&p2, 2, 1);
insert(&p2, 1, 0);

sum = add(p1, p2);
diff = subtract(p1, p2);
printf("Polynomial 1: ");
display(p1);
printf("Polynomial 2: ");
display(p2);
printf("Addition: ");
display(sum);
printf("Subtraction: ");
display(diff);
return 0;
}
Output
******* MAIN MENU *******
1. Enter the 1rst polynomial
2. Display the 1rst polynomial
–––––––––––––––––––––––––––––––
9. EXIT
Enter your option : 1
Enter the number : 6
Enter its coef cient : 2
Enter the number : 5
Enter its coef cient : 1
Enter the number : –1
Enter your option : 2
6 x 2 5 x 1
Enter your option : 9
Result:
Thus the above program to store a polynomial using linked list is created and also addition and
subtraction on two polynomials are performed successfully.

Ex. No:6 BINARY SEARCH TREE
Date:
Aim:
To construct a binary search tree and perform search.
Algorithm
1. Start
2. Call insert to insert an element into binary search tree.
3. Call delete to delete an element from binary search tree.
4. Call findmax to find the element with maximum value in binary search tree
5. Call findmin to find the element with minimum value in binary search tree
6. Call find to check the presence of the element in the binary search tree
7. Call display to display the elements of the binary search tree
8. Call makeempty to delete the entire tree.
9. Stop
Insert function
1. Get the element to be inserted.
2. Find the position in the tree where the element to be inserted by checking
the elements in the tree by traversing from the root.
3. If the element to be inserted is less than the element in the current node in
the tree then traverse left subtree
4. If the element to be inserted is greater than the element in the current node
in the tree then traverse right subtree
5. Insert the element if there is no further move
Delete function
1. Get the element to be deleted.
2. Find the node in the tree that contain the element.
3. Delete the node an rearrange the left and right siblings if any present for the
deleted node
Findmax function
1. Traverse the tree from the root.
2. Find the rightmost leaf node of the entire tree and return it
3. If the tree is empty return null.
Findmin function
1. Traverse the tree from the root.
2. Find the leftmost leaf node of the entire tree and return it
3. If the tree is empty return null.
Find function
1. Traverse the tree from the root.
2. Check whether the element to searched matches with element of the current
node. If match occurs return it.
3. Otherwise if the element is less than that of the element of the current node
then search the leaf subtree
4. Else search right subtree.
Makeempty function
Make the root of the tree to point to null.

Program
#include<stdio.h>
#include<stdlib.h>
#include<conio.h>
struct searchtree
{
int element;
struct searchtree *left,*right;
}*root;
typedef struct searchtree *node;
typedef int ElementType;
node insert(ElementType, node);
node delete(ElementType, node);
void makeempty();
node findmin(node);
node findmax(node);
node find(ElementType, node);
void display(node, int);
void main()
{
int ch;
ElementType a;
node temp;
makeempty();
while(1)
{
printf("\n1. Insert\n2. Delete\n3. Find\n4. Find min\n5. Find max\n6.Display\n7.
Exit\nEnter Your Choice : ");
scanf("%d",&ch);
switch(ch)
{
case 1:
printf("Enter an element : ");
scanf("%d", &a);
root = insert(a, root);
break;
case 2:
printf("\nEnter the element to delete : ");
scanf("%d",&a);
root = delete(a, root);
break;
case 3:
printf("\nEnter the element to search : ");
scanf("%d",&a);
temp = find(a, root);
if (temp != NULL)
printf("Element found");

else
printf("Element not found");
break;
case 4:
temp = findmin(root);
if(temp==NULL)
printf("\nEmpty tree");
else
printf("\nMinimum element : %d", temp->element);
break;
case 5:
temp = findmax(root);
if(temp==NULL)
printf("\nEmpty tree");
else
printf("\nMaximum element : %d", temp->element);
break;
case 6:
if(root==NULL)printf("\nEmpty tree");
else
display(root, 1);
break;
case 7:
exit(0);
default:
printf("Invalid Choice");
}
}
}
node insert(ElementType x,node t)
{
if(t==NULL)
{
t = (node)malloc(sizeof(node));
t->element = x;
t->left = t->right = NULL;
}
else
{
if(x < t->element)
t->left = insert(x, t->left);
else
if(x > t->element)t->right = insert(x, t->right);
}
return t;
}
node delete(ElementType x,node t)
{

node temp;
if(t == NULL)
printf("\nElement not found");
else
{
if(x < t->element)
t->left = delete(x, t->left);
else if(x > t->element)
t->right = delete(x, t->right);
else
{
if(t->left && t->right)
{
temp = findmin(t->right);
t->element = temp->element;
t->right = delete(t->element,t->right);
}
else if(t->left == NULL)
{
temp = t;
t=t->right;
free (temp);
}
else
{
temp = t;
t=t->left;
free (temp);
}
}
}
return t;
}
void makeempty()
{
root = NULL;
}
node findmin(node temp)
{
if(temp == NULL || temp->left == NULL)
return temp;
return findmin(temp->left);
}
node findmax(node temp)
{
if(temp==NULL || temp->right==NULL)
return temp;

return findmax(temp->right);
}
node find(ElementType x, node t)
{
if(t==NULL)
return NULL;
if(x<t->element)
return find(x,t->left);
if(x>t->element)
return find(x,t->right);
return t;
}
void display(node t,int level)
{
int i;
if(t)
{
display(t->right, level+1);
printf(“ \n”);
for(i=0;i<level;i++)
printf(" ");
printf("%d", t->element);
display(t->left, level+1);
}
}
Output:
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit
Enter your Choice : 1
Enter an element : 10
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit
Enter your Choice : 1

Enter an element : 20
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit
Enter your Choice : 1
Enter an element : 5
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit
Enter your Choice : 4
The smallest Number is 5
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit
Enter your Choice : 3
Enter an element : 100
Element not Found
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit
Enter your Choice : 2
Enter an element : 20
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit

Enter your Choice : 6
20
10
1. Insert
2. Delete
3. Find
4. Find Min
5. Find Max
6. Display
7. Exit
Enter your Choice : 7
Result:
Thus the above program to construct a binary search tree and to perform search operation
is implemented and verified successfully.

Ex. No:7 DIJKSTRAS ALGORITHM
Date:
Aim:
To write a C program to implement Dijkstra's Algorithm to find the shortest path
Algorithm
1. Start
2. Mark the ending vertex with a distance of zero. Designate this vertex as current.
3. Find all vertices leading to the current vertex. Calculate their distances to the end. ...
4. Mark the current vertex as visited. ...
5. Mark the vertex with the smallest distance as current, and repeat from step 2.
6. Stop
Program
#include <stdio.h>
#define INF 9999
#define MAX 10
void dijkstra(int graph[MAX][MAX], int n, int start) {
int distance[MAX], visited[MAX] = {0}, i, j, minDist, nextNode;
// Initialize distances from start to all other nodes
for (i = 0; i < n; i++) {
distance[i] = graph[start][i];
}
visited[start] = 1;
distance[start] = 0;
for (i = 1; i < n; i++) {
minDist = INF;
// Find the unvisited node with the smallest distance
for (j = 0; j < n; j++) {
if (!visited[j] && distance[j] < minDist) {
minDist = distance[j];
nextNode = j;

}
}
visited[nextNode] = 1;
// Update distances
for (j = 0; j < n; j++) {
if (!visited[j] && (minDist + graph[nextNode][j] < distance[j])) {
distance[j] = minDist + graph[nextNode][j];
}
}
}
// Print shortest distances
printf("\nShortest distances from node %d:\n", start);
for (i = 0; i < n; i++) {
printf("To node %d: %d\n", i, distance[i]);
}
}
int main() {
int graph[MAX][MAX], n, i, j, start;
printf("Enter number of nodes: ");
scanf("%d", &n);
printf("Enter the adjacency matrix (use %d for infinity):\n", INF);
for (i = 0; i < n; i++) {
for (j = 0; j < n; j++) {
scanf("%d", &graph[i][j]);
}
}
printf("Enter the starting node: ");
scanf("%d", &start);
dijkstra(graph, n, start);

return 0;
}
OUTPUT
Enter number of nodes: 5
Enter the adjacency matrix (use 9999 for infinity):
0 10 9999 30 100
10 0 50 9999 9999
9999 50 0 20 10
30 9999 20 0 60
100 9999 10 60 0
Enter the starting node: 0
Shortest distances from node 0:
To node 0: 0
To node 1: 10
To node 2: 50
To node 3: 30
To node 4: 60
Result:
T hu s t he a bo ve C program to implement Dijkstra's Algorithm to find the shortest path
is implemented and verified successfully.

Ex. No:8 PRIM’S ALGORITHM
Date:
Aim:
To write a C program for implementation of Prim's algorithm.
Algorithm:
1. Start the program.
2. Get the number of nodes & edges in the graph.
3. Get the edges v1 and v2 and then get corresponding weight.
4. Find the weight of the edge(minimum).
5. Calculate total path length.
6. Display the weight and the total path.
7. Stop the program
Program:
#include<stdio.h>
#include<conio.h>
#define SIZE 20
#define INFINITY 32767
void prim(int G[][SIZE],int nodes)
{
int Q[SIZE],i,j,k;
int min_dist,v1,v2,total=0;
for(i=0;i<nodes;i++)
Q[i]=0;
printf("\n\nThe minimal spanning tree is:\n");
Q[0]=1;
for(k=1;k<nodes;k++)
{
min_dist=INFINITY;
for(i=0;i<nodes;i++)
{
for(j=0;j<nodes;j++)
{
if(G[i][j] && ((Q[i]&&!Q[j]) || (!Q[i] && Q[j])))
{
if(G[i][j]<min_dist)

{
min_dist=G[i][j]; v1=i;
v2=j;
}
}
}
}
printf("\n edge(%d,%d) and weight= %d ",v1,v2,min_dist);
Q[v1]=Q[v2]=1;
total=total+min_dist;
}
printf("\n\n\tTotal path length is = %d ",total);
}
void main()
{
int G[SIZE][SIZE],nodes;
int v1,v2,length,i,j,n;
clrscr();
printf("\n\t Prim's Algorithm \n");
printf("Enter the number of nodes in the graph:\t");
scanf("%d",&nodes);
printf("\nEnter number of edges in the graph:\t");
scanf("%d",&n);
for(i=0;i<nodes;i++)
for(j=0;j<nodes;j++)
G[i][j]=0;
printf("\nEnter edges and weights:\t");
for(i=1;i<n;i++)
{
printf("\nEnter edge by v1 and v2 :\t");
scanf("%d%d",&v1,&v2);
printf("\nEnter corresponding weights:\t");
scanf("%d",&length);
G[v1][v2]=G[v2][v1]=length;
}
getch();
printf("\n\t");
clrscr();
prim(G,nodes);

getch();
Output:

Result:
T hu s t he a bo ve C program to implement Prims Algorithm is implemented
and verified successfully.

Ex. No:9a BINARY SEARCH
Date:
Aim
To locate an element in a sorted array using Binary search method
Algorithm
1. Start
2. Read number of array elements, say n
3. Create an array arr consisting n sorted elements
4. Get element, say key to be located
5. Assign 0 to lower and n to upper
6. While (lower < upper)
a. Determine middle element mid = (upper+lower)/2
b. If key = arr[mid] then
i. Print mid
ii. Stop
c. Else if key > arr[mid] then
i. lower = mid + 1
d. else
i. upper = mid – 1
7. Print "Element not found"
8. Stop
Program
/* Binary Search on a sorted array */
#include <stdio.h>
void main()
{
int a[50],i, n, upper, lower, mid, val, found, att=0;
printf("Enter array size : ");
scanf("%d", &n);
for(i=0; i<n; i++)
a[i] = 2 * i;
printf("\n Elements in Sorted Order \n");
for(i=0; i<n; i++)
printf("%4d", a[i]);
printf("\n Enter element to locate : ");
scanf("%d", &val);
upper = n;
lower = 0;
found = -1;
while (lower <= upper)
{
mid = (upper + lower)/2;
att++;
if (a[mid] == val)
{

printf("Found at index %d in %d attempts", mid, att);
found = 1;
break;
}
else if(a[mid] > val)
upper = mid - 1;
else
lower = mid + 1;
}
if (found == -1)
printf("Element not found");
}
Output
Enter array size : 10
Elements in Sorted Order
0 2 4 6 8 10 12 14 16 18
Enter element to locate : 16
Found at index 8 in 2 attempts
Result:
Thus the above program to locate an element in a sorted array using Binary search method
is implemented and verified successfully.

Ex. No:9b LINEAR SEARCH
Date:
Aim
To locate an element in a sorted array using Linear search method
Algorithm
1. Start
2. Set i to 1.
3. if i > n, then jump to step 7.
4.
5. if A[i] = x then jump to step 6.
6. Set i to i + 1.
7. Go to step 2.
8. Print element x found at index i and jump to step 8.
9. Print element not found.
10. Exit.
Program:
#include <stdio.h>
// Function to perform linear search
int linearSearch(int arr[], int n, int key) {
for (int i = 0; i < n; i++) {
if (arr[i] == key)
return i; // Element found at index i
}
return -1; // Element not found
}
int main() {
int n, key;
printf("Enter number of elements: ");
scanf("%d", &n);
int arr[n];
printf("Enter %d elements:\n", n);
for (int i = 0; i < n; i++) {
scanf("%d", &arr[i]);
}
printf("Enter the element to search: ");
scanf("%d", &key);
int idx = linearSearch(arr, n, key);

if (idx != -1)
printf("Element %d found at index %d\n", key, idx);
else
printf("Element %d not found in the array\n", key);
return 0;
}
OUTPUT
Enter number of elements: 5
Enter 5 elements:
10 25 30 45 60
Enter the element to search: 30
Element 30 found at index 2
Result:
Thus the above program to locate an element in a sorted array using Linear search method
is implemented and verified successfully.

Ex. No:10a INSERTION SORT
Date:
Aim:
To sort an array of N numbers using Insertion sort.
Algorithm
1. Start
2. Read number of array elements n
3. Read array elements Ai
4. Outer index i varies from second element to last element
5. Inner index j is used to compare elements to left of outer index
6. Insert the element into the appropriate position.
7. Display the array elements after each pass
8. Display the sorted array elements.
9. Stop
Program
/* 11a - Insertion Sort */
void main()
{
int i, j, k, n, temp, a[20], p=0;
printf("Enter total elements: ");
scanf("%d",&n);
printf("Enter array elements: ");
for(i=0; i<n; i++)
scanf("%d", &a[i]);
for(i=1; i<n; i++)
{
temp = a[i];
j = i - 1;
while((temp<a[j]) && (j>=0))
{
a[j+1] = a[j];
j = j - 1;
}
a[j+1] = temp;
p++;
printf("\n After Pass %d: ", p);
for(k=0; k<n; k++)
printf(" %d", a[k]);
}
printf("\n Sorted List : ");
for(i=0; i<n; i++)
printf(" %d", a[i]);
}

Output
Enter total elements: 6
Enter array elements: 34 8 64 51 32 21
After Pass 1: 8 34 64 51 32 21
After Pass 2: 8 34 64 51 32 21
After Pass 3: 8 34 51 64 32 21
After Pass 4: 8 32 34 51 64 21
After Pass 5: 8 21 32 34 51 64
Sorted List : 8 21 32 34 51 64
Result:
Thus the above program to sort an array of N numbers using Insertion sort is implemented
and verified successfully.

Ex. No:10b SELECTION SORT
Date:
Aim:
To sort an array of N numbers using selection sort.
Algorithm
1. Start
2. Set minIndex to position 0. ...
3. Search for the smallest element in the unsorted subarray and update minIndex.
4. Swap the element at the position minIndex with the first element of the unsorted subarray.
5. Again set minIndex to the first position of the unsorted subarray.
6. stop
Program
#include <stdio.h>
void selectionSort(int arr[], int n) {
int i, j, minIdx, temp;
for (i = 0; i < n - 1; i++) {
minIdx = i;
// Find the index of the minimum element
for (j = i + 1; j < n; j++) {
if (arr[j] < arr[minIdx]) {
minIdx = j;
}
}
// Swap the found minimum with the first element
if (minIdx != i) {
temp = arr[i];
arr[i] = arr[minIdx];
arr[minIdx] = temp;
}
}
}
void printArray(int arr[], int n) {
int i;
for (i = 0; i < n; i++) {
printf("%d ", arr[i]);
}
printf("\n");
}
int main() {

int arr[100], n, i;
printf("Enter the number of elements: ");
scanf("%d", &n);
printf("Enter %d elements:\n", n);
for (i = 0; i < n; i++) {
scanf("%d", &arr[i]);
}
printf("Original array:\n");
printArray(arr, n);
selectionSort(arr, n);
printf("Sorted array (Selection Sort):\n");
printArray(arr, n);
return 0;
}
Input:
Enter the number of elements: 6
Enter 6 elements:
29 10 14 37 13 5
Output:
29 10 14 37 13 5
Sorted array (Selection Sort):
5 10 13 14 29 37
Result:
Thus the above program to sort an array of N numbers using Selection sort is implemented
and verified successfully.