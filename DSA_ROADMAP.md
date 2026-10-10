# DSA Mastery Roadmap - Java Edition

## 📚 Complete Learning Path with Java Examples

---

## Phase 1: Programming Fundamentals (Week 1-2)

### 1.1 Basic Concepts
- Variables & Data Types
- Operators
- Control Flow (if-else, switch)
- Loops (for, while, do-while)

### 1.2 Functions & Methods
- Method declaration & calling
- Parameters & return types
- Scope & lifetime
- Recursion basics

### 1.3 Object-Oriented Programming
- Classes & Objects
- Constructors
- Inheritance
- Polymorphism
- Encapsulation
- Abstraction

### 1.4 Collections Framework
- ArrayList
- HashMap
- HashSet
- LinkedList
- Stack
- Queue

---

## Phase 2: Arrays & Strings (Week 3-4)

### 2.1 Arrays
**Key Topics:**
- 1D Arrays
- 2D Arrays
- Array manipulation
- Searching in arrays
- Sorting arrays

**Java Examples:**

```java
// Array Declaration
int[] arr = new int[10];
int[] arr2 = {1, 2, 3, 4, 5};

// 2D Array
int[][] matrix = new int[3][3];

// Sorting
Arrays.sort(arr);

// Searching
int index = Arrays.binarySearch(arr, target);
```

**Problems to Solve:**
1. Two Sum
2. Best Time to Buy and Sell Stock
3. Contains Duplicate
4. Product of Array Except Self
5. Maximum Subarray (Kadane's Algorithm)

### 2.2 Strings
**Key Topics:**
- String manipulation
- Substring problems
- Pattern matching
- Anagrams
- Palindromes

**Java Examples:**

```java
// String Declaration
String str = "Hello World";

// String Methods
str.length();
str.charAt(index);
str.substring(start, end);
str.indexOf(char);
str.replace(old, new);
str.toCharArray();

// String Builder for mutable strings
StringBuilder sb = new StringBuilder();
sb.append("Hello");
sb.reverse();
```

**Problems to Solve:**
1. Valid Palindrome
2. Reverse String
3. Valid Anagram
4. Group Anagrams
5. Longest Substring Without Repeating Characters

---

## Phase 3: Hashing & Hash Maps (Week 5)

### 3.1 Hash Map Concepts
**Key Topics:**
- Hash functions
- Collisions
- Load factor
- Hash Map implementation

**Java Examples:**

```java
// HashMap
HashMap<String, Integer> map = new HashMap<>();
map.put("key", value);
map.get("key");
map.remove("key");
map.containsKey("key");
map.keySet();
map.values();
map.entrySet();

// HashSet
HashSet<Integer> set = new HashSet<>();
set.add(1);
set.contains(1);
set.remove(1);

// TreeMap (sorted)
TreeMap<Integer, String> treeMap = new TreeMap<>();

// LinkedHashMap (insertion order)
LinkedHashMap<String, Integer> linkedMap = new LinkedHashMap<>();
```

**Problems to Solve:**
1. Two Sum
2. Valid Sudoku
3. Majority Element
4. Intersection of Two Arrays
5. Happy Number

---

## Phase 4: Two Pointers & Sliding Window (Week 6)

### 4.1 Two Pointers Technique
**Key Topics:**
- Two pointer approach
- Sorted array problems
- Reverse operations

**Java Examples:**

```java
// Two Pointer - Two Sum (Sorted Array)
public int[] twoSum(int[] numbers, int target) {
    int left = 0, right = numbers.length - 1;
    while (left < right) {
        int sum = numbers[left] + numbers[right];
        if (sum == target) {
            return new int[]{left + 1, right + 1};
        } else if (sum < target) {
            left++;
        } else {
            right--;
        }
    }
    return new int[]{};
}

// Reverse Array
public void reverse(int[] nums) {
    int left = 0, right = nums.length - 1;
    while (left < right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
        left++;
        right--;
    }
}
```

**Problems to Solve:**
1. Two Sum II - Input Array Is Sorted
2. Valid Palindrome
3. Container With Most Water
4. Trapping Rain Water
5. Remove Duplicates from Sorted Array

### 4.2 Sliding Window Technique
**Key Topics:**
- Window expansion
- Window contraction
- Fixed size windows
- Dynamic size windows

**Java Examples:**

```java
// Sliding Window - Longest Substring Without Repeating Characters
public int lengthOfLongestSubstring(String s) {
    HashMap<Character, Integer> map = new HashMap<>();
    int maxLen = 0, left = 0;
    
    for (int right = 0; right < s.length(); right++) {
        char c = s.charAt(right);
        if (map.containsKey(c)) {
            left = Math.max(left, map.get(c) + 1);
        }
        map.put(c, right);
        maxLen = Math.max(maxLen, right - left + 1);
    }
    return maxLen;
}

// Sliding Window - Maximum Sum of Subarray of Size K
public int maxSumSubarray(int[] arr, int k) {
    int maxSum = 0, windowSum = 0;
    
    for (int i = 0; i < k; i++) {
        windowSum += arr[i];
    }
    maxSum = windowSum;
    
    for (int i = k; i < arr.length; i++) {
        windowSum = windowSum - arr[i - k] + arr[i];
        maxSum = Math.max(maxSum, windowSum);
    }
    return maxSum;
}
```

**Problems to Solve:**
1. Longest Substring Without Repeating Characters
2. Minimum Window Substring
3. Permutation in String
4. Max Consecutive Ones III
5. Minimum Size Subarray Sum

---

## Phase 5: Sorting & Searching (Week 7)

### 5.1 Sorting Algorithms
**Key Topics:**
- Bubble Sort - O(n²)
- Selection Sort - O(n²)
- Insertion Sort - O(n²)
- Merge Sort - O(n log n)
- Quick Sort - O(n log n)
- Heap Sort - O(n log n)

**Java Examples:**

```java
// Merge Sort
public void mergeSort(int[] arr, int left, int right) {
    if (left < right) {
        int mid = left + (right - left) / 2;
        mergeSort(arr, left, mid);
        mergeSort(arr, mid + 1, right);
        merge(arr, left, mid, right);
    }
}

private void merge(int[] arr, int left, int mid, int right) {
    int[] temp = new int[right - left + 1];
    int i = left, j = mid + 1, k = 0;
    
    while (i <= mid && j <= right) {
        if (arr[i] <= arr[j]) {
            temp[k++] = arr[i++];
        } else {
            temp[k++] = arr[j++];
        }
    }
    
    while (i <= mid) temp[k++] = arr[i++];
    while (j <= right) temp[k++] = arr[j++];
    
    System.arraycopy(temp, 0, arr, left, temp.length);
}

// Quick Sort
public void quickSort(int[] arr, int low, int high) {
    if (low < high) {
        int pi = partition(arr, low, high);
        quickSort(arr, low, pi - 1);
        quickSort(arr, pi + 1, high);
    }
}

private int partition(int[] arr, int low, int high) {
    int pivot = arr[high];
    int i = low - 1;
    for (int j = low; j < high; j++) {
        if (arr[j] < pivot) {
            i++;
            int temp = arr[i];
            arr[i] = arr[j];
            arr[j] = temp;
        }
    }
    int temp = arr[i + 1];
    arr[i + 1] = arr[high];
    arr[high] = temp;
    return i + 1;
}
```

**Problems to Solve:**
1. Sort an Array
2. Merge k Sorted Lists
3. Kth Largest Element in an Array
4. Top K Frequent Elements
5. Sort Colors

### 5.2 Searching Algorithms
**Key Topics:**
- Linear Search - O(n)
- Binary Search - O(log n)
- Search in rotated array
- Search in 2D matrix

**Java Examples:**

```java
// Binary Search
public int binarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) {
            return mid;
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return -1;
}

// Binary Search (Left most position)
public int leftmostBinarySearch(int[] arr, int target) {
    int left = 0, right = arr.length - 1, result = -1;
    
    while (left <= right) {
        int mid = left + (right - left) / 2;
        if (arr[mid] == target) {
            result = mid;
            right = mid - 1;  // Continue searching left
        } else if (arr[mid] < target) {
            left = mid + 1;
        } else {
            right = mid - 1;
        }
    }
    return result;
}
```

**Problems to Solve:**
1. Binary Search
2. Search Insert Position
3. Search in Rotated Sorted Array
4. Find First and Last Position of Element in Sorted Array
5. Search a 2D Matrix

---

## Phase 6: Recursion & Backtracking (Week 8-9)

### 6.1 Recursion Fundamentals
**Key Topics:**
- Base case
- Recursive case
- Call stack
- Memoization
- Time complexity analysis

**Java Examples:**

```java
// Factorial
public int factorial(int n) {
    if (n <= 1) return 1;
    return n * factorial(n - 1);
}

// Fibonacci
public int fibonacci(int n) {
    if (n <= 1) return n;
    return fibonacci(n - 1) + fibonacci(n - 2);
}

// Fibonacci with Memoization
public int fibonacciMemo(int n, int[] memo) {
    if (n <= 1) return n;
    if (memo[n] != -1) return memo[n];
    
    memo[n] = fibonacciMemo(n - 1, memo) + fibonacciMemo(n - 2, memo);
    return memo[n];
}

// Power (a^b)
public long power(int a, int b) {
    if (b == 0) return 1;
    long half = power(a, b / 2);
    if (b % 2 == 0) {
        return half * half;
    } else {
        return half * half * a;
    }
}
```

**Problems to Solve:**
1. Factorial
2. Fibonacci
3. Power of a Number
4. Greatest Common Divisor (GCD)
5. Sum of Array

### 6.2 Backtracking
**Key Topics:**
- Permutations
- Combinations
- N-Queens
- Sudoku
- Word search
- Subsets

**Java Examples:**

```java
// Permutations
public List<List<Integer>> permute(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    backtrack(nums, new ArrayList<>(), result, new boolean[nums.length]);
    return result;
}

private void backtrack(int[] nums, List<Integer> current, 
                      List<List<Integer>> result, boolean[] used) {
    if (current.size() == nums.length) {
        result.add(new ArrayList<>(current));
        return;
    }
    
    for (int i = 0; i < nums.length; i++) {
        if (!used[i]) {
            current.add(nums[i]);
            used[i] = true;
            backtrack(nums, current, result, used);
            current.remove(current.size() - 1);
            used[i] = false;
        }
    }
}

// Combinations
public List<List<Integer>> combine(int n, int k) {
    List<List<Integer>> result = new ArrayList<>();
    backtrackCombine(1, n, k, new ArrayList<>(), result);
    return result;
}

private void backtrackCombine(int start, int n, int k, 
                             List<Integer> current, List<List<Integer>> result) {
    if (current.size() == k) {
        result.add(new ArrayList<>(current));
        return;
    }
    
    for (int i = start; i <= n; i++) {
        current.add(i);
        backtrackCombine(i + 1, n, k, current, result);
        current.remove(current.size() - 1);
    }
}

// Subsets
public List<List<Integer>> subsets(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    backtrackSubset(nums, 0, new ArrayList<>(), result);
    return result;
}

private void backtrackSubset(int[] nums, int start, 
                            List<Integer> current, List<List<Integer>> result) {
    result.add(new ArrayList<>(current));
    
    for (int i = start; i < nums.length; i++) {
        current.add(nums[i]);
        backtrackSubset(nums, i + 1, current, result);
        current.remove(current.size() - 1);
    }
}
```

**Problems to Solve:**
1. Permutations
2. Combinations
3. Generate Parentheses
4. Word Search
5. N-Queens

---

## Phase 7: Linked Lists (Week 10)

### 7.1 Linked List Basics
**Key Topics:**
- Singly linked list
- Doubly linked list
- Circular linked list
- Traversal
- Insertion & Deletion

**Java Examples:**

```java
// Node Class
class ListNode {
    int val;
    ListNode next;
    ListNode(int val) {
        this.val = val;
        this.next = null;
    }
}

// Singly Linked List
public class LinkedList {
    ListNode head;
    
    // Insert at beginning
    public void insertAtBeginning(int val) {
        ListNode newNode = new ListNode(val);
        newNode.next = head;
        head = newNode;
    }
    
    // Insert at end
    public void insertAtEnd(int val) {
        ListNode newNode = new ListNode(val);
        if (head == null) {
            head = newNode;
            return;
        }
        ListNode current = head;
        while (current.next != null) {
            current = current.next;
        }
        current.next = newNode;
    }
    
    // Delete node
    public void deleteNode(int val) {
        if (head == null) return;
        
        if (head.val == val) {
            head = head.next;
            return;
        }
        
        ListNode current = head;
        while (current.next != null) {
            if (current.next.val == val) {
                current.next = current.next.next;
                return;
            }
            current = current.next;
        }
    }
    
    // Traverse
    public void display() {
        ListNode current = head;
        while (current != null) {
            System.out.print(current.val + " -> ");
            current = current.next;
        }
        System.out.println("null");
    }
}

// Reverse Linked List
public ListNode reverseList(ListNode head) {
    ListNode prev = null, current = head;
    
    while (current != null) {
        ListNode next = current.next;
        current.next = prev;
        prev = current;
        current = next;
    }
    return prev;
}

// Merge Two Sorted Lists
public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
    ListNode dummy = new ListNode(0);
    ListNode current = dummy;
    
    while (l1 != null && l2 != null) {
        if (l1.val <= l2.val) {
            current.next = l1;
            l1 = l1.next;
        } else {
            current.next = l2;
            l2 = l2.next;
        }
        current = current.next;
    }
    
    current.next = (l1 != null) ? l1 : l2;
    return dummy.next;
}

// Detect Cycle
public boolean hasCycle(ListNode head) {
    ListNode slow = head, fast = head;
    
    while (fast != null && fast.next != null) {
        slow = slow.next;
        fast = fast.next.next;
        if (slow == fast) return true;
    }
    return false;
}
```

**Problems to Solve:**
1. Reverse Linked List
2. Merge Two Sorted Lists
3. Linked List Cycle
4. Intersection of Two Linked Lists
5. Remove Nth Node From End of List

---

## Phase 8: Stacks & Queues (Week 11)

### 8.1 Stack (LIFO - Last In First Out)
**Key Topics:**
- Push & Pop
- Parentheses matching
- Expression evaluation
- Next greater element

**Java Examples:**

```java
// Stack Implementation using ArrayList
class MyStack {
    private List<Integer> stack;
    
    public MyStack() {
        stack = new ArrayList<>();
    }
    
    public void push(int x) {
        stack.add(x);
    }
    
    public int pop() {
        if (isEmpty()) throw new EmptyStackException();
        return stack.remove(stack.size() - 1);
    }
    
    public int peek() {
        if (isEmpty()) throw new EmptyStackException();
        return stack.get(stack.size() - 1);
    }
    
    public boolean isEmpty() {
        return stack.size() == 0;
    }
}

// Valid Parentheses
public boolean isValid(String s) {
    Stack<Character> stack = new Stack<>();
    Map<Character, Character> pairs = new HashMap<>();
    pairs.put(')', '(');
    pairs.put('}', '{');
    pairs.put(']', '[');
    
    for (char c : s.toCharArray()) {
        if (pairs.containsKey(c)) {
            if (stack.isEmpty() || stack.pop() != pairs.get(c)) {
                return false;
            }
        } else {
            stack.push(c);
        }
    }
    return stack.isEmpty();
}

// Next Greater Element
public int[] nextGreaterElement(int[] nums1, int[] nums2) {
    Stack<Integer> stack = new Stack<>();
    Map<Integer, Integer> map = new HashMap<>();
    
    for (int num : nums2) {
        while (!stack.isEmpty() && stack.peek() < num) {
            map.put(stack.pop(), num);
        }
        stack.push(num);
    }
    
    int[] result = new int[nums1.length];
    for (int i = 0; i < nums1.length; i++) {
        result[i] = map.getOrDefault(nums1[i], -1);
    }
    return result;
}
```

**Problems to Solve:**
1. Valid Parentheses
2. Min Stack
3. Daily Temperatures
4. Largest Rectangle in Histogram
5. Trapping Rain Water

### 8.2 Queue (FIFO - First In First Out)
**Key Topics:**
- Enqueue & Dequeue
- Circular queue
- Priority queue
- BFS applications

**Java Examples:**

```java
// Queue Implementation using LinkedList
Queue<Integer> queue = new LinkedList<>();
queue.offer(1);      // Enqueue
queue.poll();        // Dequeue
queue.peek();        // Front element

// Priority Queue (Min Heap)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();
minHeap.offer(5);
minHeap.offer(3);
int min = minHeap.poll();  // Returns 3

// Priority Queue (Max Heap)
PriorityQueue<Integer> maxHeap = new PriorityQueue<>((a, b) -> b - a);
maxHeap.offer(5);
maxHeap.offer(3);
int max = maxHeap.poll();  // Returns 5

// Circular Queue Implementation
class CircularQueue {
    private int[] queue;
    private int front, rear, size;
    
    public CircularQueue(int k) {
        queue = new int[k];
        front = -1;
        rear = -1;
        size = 0;
    }
    
    public void enQueue(int value) {
        if (isFull()) return;
        if (front == -1) front = 0;
        rear = (rear + 1) % queue.length;
        queue[rear] = value;
        size++;
    }
    
    public int deQueue() {
        if (isEmpty()) return -1;
        int val = queue[front];
        front = (front + 1) % queue.length;
        size--;
        if (size == 0) {
            front = -1;
            rear = -1;
        }
        return val;
    }
    
    public boolean isEmpty() {
        return size == 0;
    }
    
    public boolean isFull() {
        return size == queue.length;
    }
}
```

**Problems to Solve:**
1. Implement Stack using Queues
2. Implement Queue using Stacks
3. Design Circular Queue
4. Number of Recent Calls
5. Sliding Window Maximum

---

## Phase 9: Trees & BST (Week 12-13)

### 9.1 Binary Tree
**Key Topics:**
- Tree traversal (Inorder, Preorder, Postorder)
- Level order traversal
- Height & diameter
- Path problems

**Java Examples:**

```java
// Tree Node
class TreeNode {
    int val;
    TreeNode left, right;
    TreeNode(int val) {
        this.val = val;
    }
}

// Inorder Traversal (Left -> Root -> Right)
public List<Integer> inorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    inorder(root, result);
    return result;
}

private void inorder(TreeNode node, List<Integer> result) {
    if (node == null) return;
    inorder(node.left, result);
    result.add(node.val);
    inorder(node.right, result);
}

// Preorder Traversal (Root -> Left -> Right)
public List<Integer> preorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    preorder(root, result);
    return result;
}

private void preorder(TreeNode node, List<Integer> result) {
    if (node == null) return;
    result.add(node.val);
    preorder(node.left, result);
    preorder(node.right, result);
}

// Postorder Traversal (Left -> Right -> Root)
public List<Integer> postorderTraversal(TreeNode root) {
    List<Integer> result = new ArrayList<>();
    postorder(root, result);
    return result;
}

private void postorder(TreeNode node, List<Integer> result) {
    if (node == null) return;
    postorder(node.left, result);
    postorder(node.right, result);
    result.add(node.val);
}

// Level Order Traversal (BFS)
public List<List<Integer>> levelOrder(TreeNode root) {
    List<List<Integer>> result = new ArrayList<>();
    if (root == null) return result;
    
    Queue<TreeNode> queue = new LinkedList<>();
    queue.offer(root);
    
    while (!queue.isEmpty()) {
        int levelSize = queue.size();
        List<Integer> level = new ArrayList<>();
        
        for (int i = 0; i < levelSize; i++) {
            TreeNode node = queue.poll();
            level.add(node.val);
            
            if (node.left != null) queue.offer(node.left);
            if (node.right != null) queue.offer(node.right);
        }
        result.add(level);
    }
    return result;
}

// Height of Tree
public int height(TreeNode root) {
    if (root == null) return 0;
    return 1 + Math.max(height(root.left), height(root.right));
}

// Diameter of Tree
int diameter = 0;

public int diameterOfBinaryTree(TreeNode root) {
    height(root);
    return diameter;
}

private int height(TreeNode node) {
    if (node == null) return 0;
    
    int leftHeight = height(node.left);
    int rightHeight = height(node.right);
    
    diameter = Math.max(diameter, leftHeight + rightHeight);
    return 1 + Math.max(leftHeight, rightHeight);
}

// Path Sum
public boolean hasPathSum(TreeNode root, int targetSum) {
    if (root == null) return false;
    
    if (root.left == null && root.right == null) {
        return root.val == targetSum;
    }
    
    return hasPathSum(root.left, targetSum - root.val) ||
           hasPathSum(root.right, targetSum - root.val);
}

// Maximum Path Sum
int maxSum = Integer.MIN_VALUE;

public int maxPathSum(TreeNode root) {
    maxPath(root);
    return maxSum;
}

private int maxPath(TreeNode node) {
    if (node == null) return 0;
    
    int leftSum = Math.max(0, maxPath(node.left));
    int rightSum = Math.max(0, maxPath(node.right));
    
    maxSum = Math.max(maxSum, node.val + leftSum + rightSum);
    return node.val + Math.max(leftSum, rightSum);
}
```

**Problems to Solve:**
1. Binary Tree Inorder Traversal
2. Maximum Depth of Binary Tree
3. Balanced Binary Tree
4. Binary Tree Level Order Traversal
5. Path Sum

### 9.2 Binary Search Tree (BST)
**Key Topics:**
- BST properties
- Search in BST
- Insert in BST
- Delete from BST
- Validate BST

**Java Examples:**

```java
// Search in BST
public TreeNode searchBST(TreeNode root, int val) {
    if (root == null || root.val == val) return root;
    
    if (val < root.val) {
        return searchBST(root.left, val);
    } else {
        return searchBST(root.right, val);
    }
}

// Insert in BST
public TreeNode insertIntoBST(TreeNode root, int val) {
    if (root == null) return new TreeNode(val);
    
    if (val < root.val) {
        root.left = insertIntoBST(root.left, val);
    } else {
        root.right = insertIntoBST(root.right, val);
    }
    return root;
}

// Delete from BST
public TreeNode deleteNode(TreeNode root, int key) {
    if (root == null) return null;
    
    if (key < root.val) {
        root.left = deleteNode(root.left, key);
    } else if (key > root.val) {
        root.right = deleteNode(root.right, key);
    } else {
        // Node with only one child or no child
        if (root.left == null) return root.right;
        if (root.right == null) return root.left;
        
        // Node with two children
        // Find the minimum value in right subtree (inorder successor)
        TreeNode minRight = findMin(root.right);
        root.val = minRight.val;
        root.right = deleteNode(root.right, minRight.val);
    }
    return root;
}

private TreeNode findMin(TreeNode node) {
    while (node.left != null) {
        node = node.left;
    }
    return node;
}

// Validate BST
public boolean isValidBST(TreeNode root) {
    return validate(root, Long.MIN_VALUE, Long.MAX_VALUE);
}

private boolean validate(TreeNode node, long min, long max) {
    if (node == null) return true;
    
    if (node.val <= min || node.val >= max) return false;
    
    return validate(node.left, min, node.val) &&
           validate(node.right, node.val, max);
}

// Lowest Common Ancestor in BST
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root.val > p.val && root.val > q.val) {
        return lowestCommonAncestor(root.left, p, q);
    } else if (root.val < p.val && root.val < q.val) {
        return lowestCommonAncestor(root.right, p, q);
    } else {
        return root;
    }
}
```

**Problems to Solve:**
1. Search in a Binary Search Tree
2. Insert into a Binary Search Tree
3. Delete Node in a BST
4. Validate Binary Search Tree
5. Lowest Common Ancestor of a Binary Search Tree

---

## Phase 10: Graphs (Week 14-15)

### 10.1 Graph Basics & Representations
**Key Topics:**
- Adjacency list
- Adjacency matrix
- DFS (Depth First Search)
- BFS (Breadth First Search)

**Java Examples:**

```java
// Graph using Adjacency List
public class Graph {
    private Map<Integer, List<Integer>> adj;
    
    public Graph(int vertices) {
        adj = new HashMap<>();
        for (int i = 0; i < vertices; i++) {
            adj.put(i, new ArrayList<>());
        }
    }
    
    public void addEdge(int u, int v) {
        adj.get(u).add(v);
        adj.get(v).add(u);  // For undirected graph
    }
    
    // DFS - Recursive
    public void dfs(int vertex, boolean[] visited) {
        visited[vertex] = true;
        System.out.print(vertex + " ");
        
        for (int neighbor : adj.get(vertex)) {
            if (!visited[neighbor]) {
                dfs(neighbor, visited);
            }
        }
    }
    
    // BFS - Using Queue
    public void bfs(int startVertex, int vertices) {
        boolean[] visited = new boolean[vertices];
        Queue<Integer> queue = new LinkedList<>();
        
        visited[startVertex] = true;
        queue.offer(startVertex);
        
        while (!queue.isEmpty()) {
            int vertex = queue.poll();
            System.out.print(vertex + " ");
            
            for (int neighbor : adj.get(vertex)) {
                if (!visited[neighbor]) {
                    visited[neighbor] = true;
                    queue.offer(neighbor);
                }
            }
        }
    }
}

// DFS for Detecting Cycle
public boolean hasCycleDFS(int n, List<List<Integer>> adj) {
    boolean[] visited = new boolean[n];
    boolean[] recStack = new boolean[n];
    
    for (int i = 0; i < n; i++) {
        if (!visited[i]) {
            if (dfsCycle(i, adj, visited, recStack)) {
                return true;
            }
        }
    }
    return false;
}

private boolean dfsCycle(int node, List<List<Integer>> adj, 
                        boolean[] visited, boolean[] recStack) {
    visited[node] = true;
    recStack[node] = true;
    
    for (int neighbor : adj.get(node)) {
        if (!visited[neighbor]) {
            if (dfsCycle(neighbor, adj, visited, recStack)) {
                return true;
            }
        } else if (recStack[neighbor]) {
            return true;
        }
    }
    
    recStack[node] = false;
    return false;
}

// Number of Connected Components
public int countComponents(int n, int[][] edges) {
    List<List<Integer>> adj = new ArrayList<>();
    for (int i = 0; i < n; i++) {
        adj.add(new ArrayList<>());
    }
    
    for (int[] edge : edges) {
        adj.get(edge[0]).add(edge[1]);
        adj.get(edge[1]).add(edge[0]);
    }
    
    boolean[] visited = new boolean[n];
    int components = 0;
    
    for (int i = 0; i < n; i++) {
        if (!visited[i]) {
            dfsMark(i, adj, visited);
            components++;
        }
    }
    
    return components;
}

private void dfsMark(int node, List<List<Integer>> adj, boolean[] visited) {
    visited[node] = true;
    for (int neighbor : adj.get(node)) {
        if (!visited[neighbor]) {
            dfsMark(neighbor, adj, visited);
        }
    }
}
```

**Problems to Solve:**
1. Number of Connected Components in an Undirected Graph
2. Clone Graph
3. Course Schedule (Cycle Detection)
4. Course Schedule II (Topological Sort)
5. Surrounded Regions

### 10.2 Shortest Path & Minimum Spanning Tree
**Key Topics:**
- Dijkstra's algorithm
- Floyd-Warshall
- Prim's algorithm
- Kruskal's algorithm

**Java Examples:**

```java
// Dijkstra's Algorithm
public int[] dijkstra(int[][] graph, int start) {
    int n = graph.length;
    int[] dist = new int[n];
    boolean[] visited = new boolean[n];
    
    for (int i = 0; i < n; i++) {
        dist[i] = Integer.MAX_VALUE;
    }
    dist[start] = 0;
    
    for (int i = 0; i < n; i++) {
        int u = -1;
        for (int j = 0; j < n; j++) {
            if (!visited[j] && (u == -1 || dist[j] < dist[u])) {
                u = j;
            }
        }
        
        visited[u] = true;
        
        for (int v = 0; v < n; v++) {
            if (graph[u][v] != 0 && dist[u] + graph[u][v] < dist[v]) {
                dist[v] = dist[u] + graph[u][v];
            }
        }
    }
    return dist;
}

// Dijkstra using Priority Queue (More Efficient)
public int[] dijkstraPQ(List<List<int[]>> adj, int start, int n) {
    int[] dist = new int[n];
    Arrays.fill(dist, Integer.MAX_VALUE);
    dist[start] = 0;
    
    PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[0] - b[0]);
    pq.offer(new int[]{0, start});
    
    while (!pq.isEmpty()) {
        int[] curr = pq.poll();
        int d = curr[0], u = curr[1];
        
        if (d > dist[u]) continue;
        
        for (int[] edge : adj.get(u)) {
            int v = edge[0], w = edge[1];
            if (dist[u] + w < dist[v]) {
                dist[v] = dist[u] + w;
                pq.offer(new int[]{dist[v], v});
            }
        }
    }
    return dist;
}

// Union-Find (Disjoint Set Union)
class UnionFind {
    int[] parent, rank;
    
    public UnionFind(int n) {
        parent = new int[n];
        rank = new int[n];
        for (int i = 0; i < n; i++) {
            parent[i] = i;
        }
    }
    
    public int find(int x) {
        if (parent[x] != x) {
            parent[x] = find(parent[x]);  // Path compression
        }
        return parent[x];
    }
    
    public boolean union(int x, int y) {
        int px = find(x), py = find(y);
        if (px == py) return false;
        
        // Union by rank
        if (rank[px] < rank[py]) {
            parent[px] = py;
        } else if (rank[px] > rank[py]) {
            parent[py] = px;
        } else {
            parent[py] = px;
            rank[px]++;
        }
        return true;
    }
}

// Kruskal's Algorithm for MST
public int minimumCost(int n, int[][] edges) {
    Arrays.sort(edges, (a, b) -> a[2] - b[2]);
    
    UnionFind uf = new UnionFind(n);
    int cost = 0, edgeCount = 0;
    
    for (int[] edge : edges) {
        if (uf.union(edge[0], edge[1])) {
            cost += edge[2];
            edgeCount++;
            if (edgeCount == n - 1) break;
        }
    }
    
    return edgeCount == n - 1 ? cost : -1;
}
```

**Problems to Solve:**
1. Network Delay Time (Dijkstra's)
2. Minimum Cost to Connect All Points (MST)
3. Path with Maximum Probability
4. Cheapest Flights Within K Stops
5. Course Schedule II (Topological Sort)

---

## Phase 11: Dynamic Programming (Week 16-17)

### 11.1 DP Fundamentals
**Key Topics:**
- Overlapping subproblems
- Optimal substructure
- Memoization vs Tabulation
- 1D DP
- 2D DP

**Java Examples:**

```java
// Fibonacci - Memoization (Top-Down)
public int fib(int n, int[] memo) {
    if (n <= 1) return n;
    if (memo[n] != -1) return memo[n];
    
    memo[n] = fib(n - 1, memo) + fib(n - 2, memo);
    return memo[n];
}

// Fibonacci - Tabulation (Bottom-Up)
public int fibTab(int n) {
    if (n <= 1) return n;
    
    int[] dp = new int[n + 1];
    dp[1] = 1;
    
    for (int i = 2; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

// Climbing Stairs
public int climbStairs(int n) {
    if (n <= 1) return n;
    
    int[] dp = new int[n + 1];
    dp[1] = 1;
    dp[2] = 2;
    
    for (int i = 3; i <= n; i++) {
        dp[i] = dp[i - 1] + dp[i - 2];
    }
    return dp[n];
}

// Coin Change (Minimum coins)
public int coinChange(int[] coins, int amount) {
    int[] dp = new int[amount + 1];
    Arrays.fill(dp, Integer.MAX_VALUE);
    dp[0] = 0;
    
    for (int i = 1; i <= amount; i++) {
        for (int coin : coins) {
            if (coin <= i && dp[i - coin] != Integer.MAX_VALUE) {
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
            }
        }
    }
    return dp[amount] == Integer.MAX_VALUE ? -1 : dp[amount];
}

// 0/1 Knapsack Problem
public int knapsack01(int[] weights, int[] values, int capacity) {
    int n = weights.length;
    int[][] dp = new int[n + 1][capacity + 1];
    
    for (int i = 1; i <= n; i++) {
        for (int w = 1; w <= capacity; w++) {
            if (weights[i - 1] <= w) {
                dp[i][w] = Math.max(
                    values[i - 1] + dp[i - 1][w - weights[i - 1]],
                    dp[i - 1][w]
                );
            } else {
                dp[i][w] = dp[i - 1][w];
            }
        }
    }
    return dp[n][capacity];
}

// Longest Increasing Subsequence
public int lengthOfLIS(int[] nums) {
    int n = nums.length;
    int[] dp = new int[n];
    Arrays.fill(dp, 1);
    
    for (int i = 1; i < n; i++) {
        for (int j = 0; j < i; j++) {
            if (nums[j] < nums[i]) {
                dp[i] = Math.max(dp[i], dp[j] + 1);
            }
        }
    }
    
    return Arrays.stream(dp).max().orElse(1);
}
```

**Problems to Solve:**
1. Climbing Stairs
2. House Robber
3. Coin Change
4. Longest Increasing Subsequence
5. Edit Distance

### 11.2 Advanced DP Patterns
**Key Topics:**
- 2D DP (Matrix problems)
- String DP
- Interval DP
- Bit manipulation DP

**Java Examples:**

```java
// Unique Paths (2D Grid)
public int uniquePaths(int m, int n) {
    int[][] dp = new int[m][n];
    
    for (int i = 0; i < m; i++) {
        for (int j = 0; j < n; j++) {
            if (i == 0 || j == 0) {
                dp[i][j] = 1;
            } else {
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1];
            }
        }
    }
    return dp[m - 1][n - 1];
}

// Edit Distance (Levenshtein Distance)
public int editDistance(String word1, String word2) {
    int m = word1.length(), n = word2.length();
    int[][] dp = new int[m + 1][n + 1];
    
    for (int i = 0; i <= m; i++) dp[i][0] = i;
    for (int j = 0; j <= n; j++) dp[0][j] = j;
    
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (word1.charAt(i - 1) == word2.charAt(j - 1)) {
                dp[i][j] = dp[i - 1][j - 1];
            } else {
                dp[i][j] = 1 + Math.min(
                    Math.min(dp[i - 1][j], dp[i][j - 1]),
                    dp[i - 1][j - 1]
                );
            }
        }
    }
    return dp[m][n];
}

// Longest Common Subsequence
public int longestCommonSubsequence(String text1, String text2) {
    int m = text1.length(), n = text2.length();
    int[][] dp = new int[m + 1][n + 1];
    
    for (int i = 1; i <= m; i++) {
        for (int j = 1; j <= n; j++) {
            if (text1.charAt(i - 1) == text2.charAt(j - 1)) {
                dp[i][j] = dp[i - 1][j - 1] + 1;
            } else {
                dp[i][j] = Math.max(dp[i - 1][j], dp[i][j - 1]);
            }
        }
    }
    return dp[m][n];
}

// Matrix Chain Multiplication (Interval DP)
public int matrixChainOrder(int[] p) {
    int n = p.length - 1;
    int[][] dp = new int[n][n];
    
    for (int len = 2; len <= n; len++) {
        for (int i = 0; i <= n - len; i++) {
            int j = i + len - 1;
            dp[i][j] = Integer.MAX_VALUE;
            
            for (int k = i; k < j; k++) {
                int cost = dp[i][k] + dp[k + 1][j] + p[i] * p[k + 1] * p[j + 1];
                dp[i][j] = Math.min(dp[i][j], cost);
            }
        }
    }
    return dp[0][n - 1];
}
```

**Problems to Solve:**
1. Unique Paths
2. Unique Paths II
3. Minimum Path Sum
4. Edit Distance
5. Longest Common Subsequence

---

## Phase 12: Advanced Topics (Week 18+)

### 12.1 Greedy Algorithms
**Key Topics:**
- Activity selection
- Huffman coding
- Fractional knapsack
- Interval scheduling

**Problems:**
1. Activity Selection
2. Huffman Coding
3. Jump Game
4. Jump Game II
5. Video Stitching

### 12.2 Segment Trees & Fenwick Trees
**Problems:**
1. Range Sum Query - Immutable
2. Range Sum Query - Mutable
3. Count of Smaller Numbers After Self
4. Reverse Pairs

### 12.3 Tries
**Problems:**
1. Implement Trie
2. Word Search II
3. Longest Word in Dictionary
4. Autocomplete System

---

## 📊 Study Timeline

| Week | Topics | Problems |
|------|--------|----------|
| 1-2 | Fundamentals, OOP, Collections | 5-10 |
| 3-4 | Arrays, Strings | 15-20 |
| 5 | Hashing, HashMap | 10-15 |
| 6 | Two Pointers, Sliding Window | 20-25 |
| 7 | Sorting, Searching | 15-20 |
| 8-9 | Recursion, Backtracking | 20-30 |
| 10 | Linked Lists | 15-20 |
| 11 | Stacks, Queues | 15-20 |
| 12-13 | Trees, BST | 25-30 |
| 14-15 | Graphs, BFS/DFS, Shortest Path | 25-30 |
| 16-17 | Dynamic Programming | 30-40 |
| 18+ | Advanced Topics | 20-30 |

**Total: ~300-400 Problems**

---

## 🎯 Coding Tips

### For Every Problem
1. **Understand** - Read 2-3 times
2. **Plan** - Write pseudocode
3. **Code** - Implement
4. **Test** - With examples + edge cases
5. **Optimize** - Improve time/space

### Common Patterns
- **Two Pointers** - Use for sorted arrays
- **Sliding Window** - Use for contiguous subarrays
- **HashMap** - Use for fast lookups
- **BFS** - Use for shortest path (unweighted)
- **DFS** - Use for traversal/exploration
- **DP** - Use when overlapping subproblems exist
- **Greedy** - Use when locally optimal works

### Complexity Cheat Sheet
| Operation | Time |
|-----------|------|
| Array Access | O(1) |
| Array Insert/Delete | O(n) |
| HashMap Get/Put | O(1) |
| LinkedList Insert/Delete | O(1) |
| Sorting | O(n log n) |
| Binary Search | O(log n) |
| Tree Traversal | O(n) |
| Graph BFS/DFS | O(V + E) |

---

## 📚 Resources

### Online Platforms
- LeetCode - Best for practice
- Codeforces - Best for competitions
- HackerRank - Interactive learning
- GeeksforGeeks - Concept explanations
- InterviewBit - Interview preparation

### Java-Specific
- Java Collections Framework documentation
- Java Stream API for functional programming
- ArrayDeque for better performance than Stack/Queue
- TreeSet/TreeMap for sorted collections

### Books
- "Data Structures and Algorithms Made Easy" - Narasimha Karumanchi
- "Introduction to Algorithms" (CLRS) - Advanced reference
- "Cracking the Coding Interview" - Interview prep

---

## ✅ Checklist for Mastery

- [ ] Understand time/space complexity analysis
- [ ] Master all fundamental DS (Array, String, Hash, List, Stack, Queue)
- [ ] Comfortable with 2-pointer and sliding window
- [ ] Can implement sorting algorithms
- [ ] Comfortable with recursion and backtracking
- [ ] Tree and BST problems feel natural
- [ ] Graph problems (BFS, DFS, shortest path) clear
- [ ] DP problems systematic approach
- [ ] Can solve medium LeetCode problems in 30 mins
- [ ] Can solve hard problems with hints
- [ ] Written optimized, clean code
- [ ] Explain solutions clearly

---

**Remember:** Consistency > Intensity. Code every day, even if it's 30 minutes. In 3-6 months of dedicated practice, you'll become proficient in DSA!
