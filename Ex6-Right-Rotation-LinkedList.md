# Ex6 Right Rotation LinkedList
## DATE:07.02.2026        
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.
## Algorithm
1. start the program.
2. Handle edge cases.
3. Find the length of the linked list.
4. Connect last node to head (make circular list).
5. Normalize k and find the new tail position.
6. Break the circle to form new list and return newHead.
7. Stop the program. 

## Program:
```
/*
Program to  Right Rotation LinkedList
Developed by: KIRANBALAJI H
RegisterNumber:  212223040096
*/
```
```
import java.util.Scanner;
public class RotateLinkedList {

    public static Node rotate(Node head, int k) {
        if (head == null || k == 0) {
            return head;
        }

        Node temp = head;
        int length = 1;

        while (temp.next != null) {
            temp = temp.next;
            length++;
        }

        temp.next = head; 

        k = k % length;
        int steps = length - k;

        Node newTail = head;
        for (int i = 1; i < steps; i++) {
            newTail = newTail.next;
        }

        Node newHead = newTail.next;
        newTail.next = null;

        return newHead;
    }

    public static void display(Node head) {
        Node current = head;
        System.out.print("LinkedList: ");
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Node head = null, tail = null;
        int n = scanner.nextInt();

        for (int i = 0; i < n; i++) {
            Node newNode = new Node(scanner.nextInt());
            if (head == null) {
                head = tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }

        int k = scanner.nextInt();
        head = rotate(head, k);
        display(head);
        scanner.close();
    }
}

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}
```

## Output:
<img width="758" height="292" alt="image" src="https://github.com/user-attachments/assets/94c22000-552b-4b2e-adeb-531b84fa0d84" />

## Result:
Thus, the C program to perfom right rotation on linked list is implemented successfully.
