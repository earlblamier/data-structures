1. Array
A fixed-size collection of elements stored in contiguous memory locations.
Example: [1, 2, 3, 4, 5]
Use Cases: Searching, sorting, and storing data in a fixed-size structure.

3. Linked List
A sequence of nodes where each node contains data and a reference (pointer) to the next node.
Types: Singly Linked List, Doubly Linked List, Circular Linked List.
Use Cases: Implementing stacks, queues, and dynamic memory allocation.

5. Stack (LIFO - Last In, First Out)
A linear data structure where the last inserted element is the first to be removed.
Operations: push(), pop(), peek().
Use Cases: Undo/Redo operations, expression evaluation, function calls (recursion).

7. Queue (FIFO - First In, First Out)
Elements are added at the rear and removed from the front.
Types: Simple Queue, Circular Queue, Priority Queue, Deque (Double-ended Queue).
Use Cases: Scheduling tasks, print spooling, breadth-first search (BFS).

9. Hash Table / Hash Map
Stores key-value pairs with efficient lookup, insertion, and deletion using a hash function.
Use Cases: Implementing dictionaries, caching, and database indexing.

11. Heap (Priority Queue)
A specialized tree-based data structure used for fast retrieval of the maximum or minimum element.
Types: Min Heap, Max Heap.
Use Cases: Dijkstra’s algorithm, priority scheduling, memory management.

13. Graph
A collection of nodes (vertices) and edges that connect them.
Types: Directed, Undirected, Weighted, Unweighted, Cyclic, Acyclic.
Use Cases: Social networks, shortest path algorithms, dependency resolution.

15. Trie (Prefix Tree)
A tree-like structure used for fast retrieval of strings with common prefixes.
Use Cases: Autocomplete, dictionary word searches, IP routing.

# data-structures
Data Structures
using System;
using System.Collections.Generic;

class Program {
    static void Main() {
        // 1. Array
        int[] numbers = {1, 2, 3, 4, 5};
        Console.WriteLine(numbers[2]); // Output: 3

        // 2. Linked List
        LinkedList<int> list = new LinkedList<int>();
        list.AddLast(1);
        list.AddLast(2);
        list.AddLast(3);
        Console.WriteLine(list.First.Value); // Output: 1

        // 3. Stack
        Stack<int> stack = new Stack<int>();
        stack.Push(10);
        stack.Push(20);
        Console.WriteLine(stack.Pop()); // Output: 20

        // 4. Queue
        Queue<int> queue = new Queue<int>();
        queue.Enqueue(10);
        queue.Enqueue(20);
        Console.WriteLine(queue.Dequeue()); // Output: 10

        // 5. Hash Table (Dictionary in C#)
        Dictionary<string, int> map = new Dictionary<string, int>();
        map["Alice"] = 25;
        map["Bob"] = 30;
        Console.WriteLine(map["Alice"]); // Output: 25

        // 6. Heap (Priority Queue in .NET 6+)
        PriorityQueue<string, int> pq = new PriorityQueue<string, int>();
        pq.Enqueue("Task1", 2);
        pq.Enqueue("Task2", 1);
        Console.WriteLine(pq.Dequeue()); // Output: Task2 (lowest priority first)

        // 7. Graph (Adjacency List Representation)
        Dictionary<int, List<int>> graph = new Dictionary<int, List<int>>();
        graph[1] = new List<int> {2, 3};
        graph[2] = new List<int> {4};
        graph[3] = new List<int> {4, 5};
        Console.WriteLine(string.Join(", ", graph[1])); // Output: 2, 3

        // 8. Trie (Prefix Tree)
        Trie trie = new Trie();
        trie.Insert("apple");
        Console.WriteLine(trie.Search("apple")); // Output: True
        Console.WriteLine(trie.Search("app"));   // Output: False
    }
}

class TrieNode {
    public Dictionary<char, TrieNode> Children = new Dictionary<char, TrieNode>();
    public bool IsEndOfWord = false;
}

class Trie {
    private TrieNode root = new TrieNode();

    public void Insert(string word) {
        TrieNode node = root;
        foreach (char c in word) {
            if (!node.Children.ContainsKey(c)) {
                node.Children[c] = new TrieNode();
            }
            node = node.Children[c];
        }
        node.IsEndOfWord = true;
    }

    public bool Search(string word) {
        TrieNode node = root;
        foreach (char c in word) {
            if (!node.Children.ContainsKey(c)) return false;
            node = node.Children[c];
        }
        return node.IsEndOfWord;
    }
}
