# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List
## DATE: 07.02.2026
## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
## Algorithm
1. Start the program.
2. Read input & build linked list.
3. If pos >= 0, link last node to pos node.
4. Use Floyd’s algorithm to detect cycle.
5. If no cycle → print "no cycle".
6. If cycle detected:
         Move second pointer from head until it meets slow pointer.
         That meeting point is cycle start.
7. Find index of that node in nodeList. 
8. Print "tail connects to node index X".
9. Stop the program.

## Program:
```
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: KIRANBALAJI H
RegisterNumber:  212223040096
*/
```
```
import java.util.*;

public class Solution {

    static class ListNode {
        int val;
        ListNode next;

        ListNode(int x) {
            val = x;
            next = null;
        }
    }

    public ListNode detectCycle(ListNode head) {
    if (head == null) return null;

    ListNode slow = head;
    ListNode fast = head;

    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;

        if (slow == fast) { 
            ListNode entry = head;
            while (entry != slow) {
                entry = entry.next;
                slow = slow.next;
            }
            return entry; 
        }
    }

    return null; 
}
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution sol = new Solution();

        String headInput = sc.nextLine().trim().replaceAll("\\[|\\]", "");
        
        int pos = sc.nextInt();

        if (headInput.isEmpty()) {
            System.out.println("no cylce");
            return;
        }

        String[] parts = headInput.split(",");
        int[] values = Arrays.stream(parts).mapToInt(Integer::parseInt).toArray();

        ListNode head = new ListNode(values[0]);
        ListNode current = head;
        List<ListNode> nodeList = new ArrayList<>();
        nodeList.add(head);

        for (int i = 1; i < values.length; i++) {
            ListNode newNode = new ListNode(values[i]);
            current.next = newNode;
            current = newNode;
            nodeList.add(newNode);
        }

      
        if (pos >= 0 && pos < nodeList.size()) {
            current.next = nodeList.get(pos);
        }


        ListNode cycleStart = sol.detectCycle(head);

        if (cycleStart != null) {
            int index = 0;
            for (ListNode node : nodeList) {
                if (node == cycleStart) {
                    System.out.println("tail connects to node index " + index);
                    return;
                }
                index++;
            }
        } else {
            System.out.println("no cycle");
        }
    }
}
```

## Output:
<img width="845" height="333" alt="image" src="https://github.com/user-attachments/assets/0e16834b-6d90-4b0c-9e2d-d4edd060762b" />

## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
