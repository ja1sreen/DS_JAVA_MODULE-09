# Ex16 Check for Balanced Parentheses Using Stack
## DATE: 11.08.2026
## AIM:
To write a Java program that verifies whether the parentheses (brackets) in an input string are balanced — meaning each opening bracket (, {, [ has a corresponding and correctly ordered closing bracket ), }, ].

## Algorithm
1. Start the program.
2. Stack Initialization.
3. Read the input string.
4. Create a stack st of size expr.length().
5. Repeat for each character in the string.
6. Opening Parentheses.
7.  Closing Parentheses.
8.  After Processing All Characters, if the stack is empty return true.
9.  If stack is not empty return false.
10.  Print the result.
11.  End the program. 

## Program:
```
/*
Program to verify whether the parentheses (brackets) in an input string are balanced
Developed by: JAISREE N
RegisterNumber: 212224060104
*/
```
```
import java.util.Scanner;

class ArrayStack {
    private char[] arr;
    private int top;

    public ArrayStack(int size) {
        arr = new char[size];
        top = -1;
    }

    public void push(char c) {
        arr[++top] = c;
    }

    public char pop() {
        return arr[top--];
    }

    public boolean isEmpty() {
        return top == -1;
    }
}

public class ParenChecker {

    public static boolean isBalanced(String expr) {
        ArrayStack st = new ArrayStack(expr.length());
        for (char ch : expr.toCharArray()) {
            if (ch == '(' || ch == '{' || ch == '[') {
                st.push(ch);
            } else if (ch == ')' || ch == '}' || ch == ']') {
                if (st.isEmpty()) return false;
                char top = st.pop();
                if ((ch == ')' && top != '(') ||
                    (ch == '}' && top != '{') ||
                    (ch == ']' && top != '[')) {
                    return false;
                }
            }
        }
        return st.isEmpty();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        String expr = sc.nextLine();
        boolean ok = isBalanced(expr);
        System.out.println(ok);
        sc.close();
    }
}
```

## Output:
<img width="410" height="312" alt="image" src="https://github.com/user-attachments/assets/a104811b-5136-46f1-803b-c687d16e8043" />

## Result:
Thus,the program correctly checks whether an input string has balanced parentheses using a stack.

# Ex17 Reversing a String Using Stack Data Structure
## DATE: 11.08.2026
## AIM:
To write a Java program that reverses an input string using a stack, without using built-in reverse functions.

## Algorithm
1. Start the program.
2. Create an empty stack of characters.
3. Traverse each character ch in the input string.
4. Create an empty StringBuilder named reversed.
5. While the stack is not empty.
6. Convert reversed to a string and return it.
7. Read the string input from the user.
8. Call and store the returned result in reversed.
9. Print the reversed string.
10. End the program.   

## Program:
```
/*
Program to reverses an input string using a stack
Developed by: JAISREE N
RegisterNumber: 212224060104
*/
```
```
import java.util.Scanner;
import java.util.Stack;

public class ReverseStringWithStack {

    public static String reverseString(String input) {
        Stack<Character> stack = new Stack<>();

        for (int i = 0; i < input.length(); i++) {
            stack.push(input.charAt(i));
        }

        StringBuilder result = new StringBuilder();

        while (!stack.isEmpty()) {
            result.append(stack.pop());
        }

        return result.toString();
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String input = scanner.nextLine();

        String reversed = reverseString(input);

        System.out.println(reversed);

        scanner.close();
    }
}
```

## Output:
<img width="381" height="285" alt="image" src="https://github.com/user-attachments/assets/14b1931b-1511-4bd7-a0ec-e06d9e95944c" />

## Result:
Thus, the program successfully reverses the given string using a stack without relying on built-in reverse functions.

# Ex18 Simulation of a Ticket Counter Using Queue (Linked List Implementation)
## DATE: 11.08.2026
## AIM:
To simulate the functioning of a ticket counter that operates on a First-In-First-Out (FIFO) basis using a queue implemented via a linked list in Java.
## Algorithm
1. Start program.
2. Queue Initialization.
3. Queue Operations.
4. DISPLAY Operation.
5. Main Simulation.
6. End the program. 

## Program:
```
/*
Program to functioning of a ticket counter that operates on a First-In-First-Out (FIFO)
Developed by: JAISREE N
RegisterNumber: 212224060104
*/
```
```
import java.util.Scanner;

class Node {
    String customerName;
    Node next;

    public Node(String name) {
        this.customerName = name;
        this.next = null;
    }
}

class TicketQueue {
    private Node front;
    private Node rear;

    public TicketQueue() {
        this.front = this.rear = null;
    }

    public void enqueue(String customerName) {
        Node newNode = new Node(customerName);

        if (front == null) {
            front = rear = newNode;
        } else {
            rear.next = newNode;
            rear = newNode;
        }
    }

    public void dequeue() {
        if (front == null) {
            System.out.println("Queue is empty. No customer to serve.");
            return;
        }

        System.out.println("Serving customer: " + front.customerName);
        front = front.next;

        if (front == null) rear = null;
    }

    public void displayQueue() {
        if (front == null) {
            System.out.println("Queue is empty.");
            return;
        }

        Node temp = front;
        System.out.print("Queue: ");
        while (temp != null) {
            System.out.print(temp.customerName);
            if (temp.next != null) System.out.print(" -> ");
            temp = temp.next;
        }
        System.out.println();
    }
}

public class TicketCounter {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        TicketQueue queue = new TicketQueue();

        while (scanner.hasNextLine()) {
            String command = scanner.nextLine().trim();
            if (command.isEmpty()) continue;

            String[] parts = command.split(" ");

            if (parts[0].equals("enqueue")) {
                if (parts.length >= 2) queue.enqueue(parts[1]);
            }
            else if (parts[0].equals("dequeue")) {
                queue.dequeue();
            }
            else if (parts[0].equals("display")) {
                queue.displayQueue();
            }
            else if (parts[0].equals("exit")) {
                System.out.println("Exiting simulation.");
                break;
            }
        }

        scanner.close();
    }
}
```

## Output:
<img width="1104" height="808" alt="image" src="https://github.com/user-attachments/assets/fe70263b-931a-47b1-adc1-c528c50f5de7" />

## Result:
Thus, the program successfully simulates a ticket counter queue where customers are served in FIFO order using a linked list-based queue implementation.

# Ex19 Palindrome Check Using Deque
## DATE: 11.08.2026
## AIM:
To design a program that checks whether a given message is a palindrome by removing all non-alphanumeric characters, converting all characters to lowercase, and using a deque data structure for comparison.

## Algorithm
1. Start the program.
2. Read the input string message.
3. Convert the string to lowercase.
4. Remove all non-alphanumeric characters using a regular expression.
5. Create an empty Deque (double-ended queue).
6. For each character c in the cleaned string.
7. While the deque contains more than one character.
8. If all pairs matched (or string has 0/1 character), return true.
9. If return value is true → print "Palindrome" , Otherwise → print "Not a palindrome".
10. End the program.      

## Program:
```
/*
Program to checks whether a given message is a palindrome by removing all non-alphanumeric characters.
Developed by: JAISREE N
RegisterNumber: 212224060104
*/
```
```
import java.util.*;

public class PalindromeChecker {
    
    public static boolean isPalindrome(String message) {
        StringBuilder cleaned = new StringBuilder();

        for (int i = 0; i < message.length(); i++) {
            char c = message.charAt(i);
            if (Character.isLetterOrDigit(c)) {
                cleaned.append(Character.toLowerCase(c));
            }
        }

        Deque<Character> deque = new ArrayDeque<>();

        for (int i = 0; i < cleaned.length(); i++) {
            deque.addLast(cleaned.charAt(i));
        }

        while (deque.size() > 1) {
            if (!deque.removeFirst().equals(deque.removeLast())) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        String input = scanner.nextLine();

        if (isPalindrome(input)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not a palindrome");
        }

        scanner.close();
    }
}
```

## Output:
<img width="433" height="282" alt="image" src="https://github.com/user-attachments/assets/4242dec0-5998-46ba-8123-f33ddbf742d6" />

## Result:
The program successfully removes all non-alphanumeric characters, converts the text to lowercase, and uses a deque to efficiently compare characters from both ends. Hence, it determines whether the string is a palindrome.

# Ex20 Sorting an Array using Merge Sort Algorithm
## DATE: 11.08.2026
## AIM:
To design a program that sorts a given array of integers in ascending order without using built-in sorting functions, achieving O(n log n) time complexity and minimal space usage.
## Algorithm
1. Start the program.
2. Read integer n.
3. Create an array nums of size n.
4. Read n integers from the user and store them into nums.
5. Call the function sortArray(nums).
6. Call heapSort(nums).
7. Return the sorted array.
8. Build Max Heap.
9. Extract Elements One by One.
10. End the program. 

## Program:
```
/*
Program tosorts a given array of integers in ascending order without using built-in sorting functions
Name : JAISREE N
RegisterNumber: 212224060104
*/
```
```
import java.util.*;

public class Solution {
    
    private void swap(int[] arr, int index1, int index2) {
        int temp = arr[index1];
        arr[index1] = arr[index2];
        arr[index2] = temp;
    }

    private void heapify(int[] arr, int n, int i) {
        int largest = i;
        int left = 2 * i + 1;
        int right = 2 * i + 2;

        if (left < n && arr[left] > arr[largest]) largest = left;
        if (right < n && arr[right] > arr[largest]) largest = right;

        if (largest != i) {
            swap(arr, i, largest);
            heapify(arr, n, largest);
        }
    }

    private void heapSort(int[] arr) {
        int n = arr.length;

        for (int i = n / 2 - 1; i >= 0; i--) {
            heapify(arr, n, i);
        }

        for (int i = n - 1; i > 0; i--) {
            swap(arr, 0, i);
            heapify(arr, i, 0);
        }
    }

    public int[] sortArray(int[] nums) {
        heapSort(nums);
        return nums;
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Solution solution = new Solution();

        int n = sc.nextInt();
        
        int[] nums = new int[n];
        for (int i = 0; i < n; i++) {
            nums[i] = sc.nextInt();
        }

        int[] sorted = solution.sortArray(nums);
        System.out.println("Sorted array:");
        System.out.println(Arrays.toString(sorted));

        sc.close();
    }
}
```

## Output:
<img width="583" height="326" alt="image" src="https://github.com/user-attachments/assets/7628e3f3-1be2-4528-9688-8facb62b5543" />

## Result:
The program has been successfully implemented and executed.
It sorts the given array of integers in ascending order using the Merge Sort algorithm with a time complexity of O(n log n) and minimal extra space.
