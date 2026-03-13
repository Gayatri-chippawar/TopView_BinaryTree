# 🌳 Top View of a Binary Tree (Java)

## 📌 Overview

This project demonstrates how to print the **Top View of a Binary Tree** using **Level Order Traversal (BFS)** and **Horizontal Distance mapping** in Java.

The **Top View** of a binary tree consists of the nodes that are visible when the tree is viewed **from the top**.

To solve this problem, we use:

* **Queue (for BFS traversal)**
* **HashMap (to store the first node at each horizontal distance)**

---

# 🌿 Example Tree

```id="tree_topview"
        1
       / \
      2   3
     / \ / \
    4  5 6  7
```

### Top View of the Tree

```id="output_top"
4 2 1 3 7
```

These nodes are visible when the tree is viewed **from above**.

---

# 📏 Key Concept: Horizontal Distance (HD)

Each node is assigned a **horizontal distance from the root**.

| Node        | Horizontal Distance |
| ----------- | ------------------- |
| Root        | 0                   |
| Left Child  | HD - 1              |
| Right Child | HD + 1              |

Example:

```id="hd_example"
        1(0)
       /   \
   2(-1)   3(+1)
    /         \
 4(-2)        7(+2)
```

The **first node encountered at each HD** forms the **top view**.

---

# ⚙️ Algorithm

1️⃣ Start BFS traversal using a **Queue**.
2️⃣ Store node and horizontal distance together.
3️⃣ Use a **HashMap** to store the first node for each horizontal distance.
4️⃣ Track the **minimum and maximum horizontal distances**.
5️⃣ Print nodes from **min HD to max HD**.

---

# 💻 Java Implementation

### Info Class (Node + Horizontal Distance)

```java id="code_info"
static class Info{
    Node node;
    int horDis;

    public Info(Node node , int hd){
        this.node = node;
        this.horDis = hd;
    }
}
```

---

### Top View Function

```java id="code_topview"
public static void topView(Node root){

    Queue<Info> q = new LinkedList<>();
    HashMap<Integer,Node> map = new HashMap<>();

    int min = 0, max = 0;

    q.add(new Info(root,0));

    while(!q.isEmpty()){

        Info curr = q.remove();

        if(!map.containsKey(curr.horDis)){
            map.put(curr.horDis, curr.node);
        }

        if(curr.node.left != null){
            q.add(new Info(curr.node.left, curr.horDis - 1));
            min = Math.min(min, curr.horDis - 1);
        }

        if(curr.node.right != null){
            q.add(new Info(curr.node.right, curr.horDis + 1));
            max = Math.max(max, curr.horDis + 1);
        }
    }

    for(int i = min; i <= max; i++){
        System.out.print(map.get(i).data + " ");
    }
}
```

---

# ▶️ Program Output

```id="top_output"
4 2 1 3 7
```

---

# ⏱ Time and Space Complexity

| Complexity       | Value |
| ---------------- | ----- |
| Time Complexity  | O(n)  |
| Space Complexity | O(n)  |

Where **n** is the number of nodes in the tree.

---

# 🧠 Concepts Used

* 🌳 Binary Trees
* 🔁 Breadth First Search (BFS)
* 📊 Queue Data Structure
* 🗺 HashMap for Horizontal Distance Mapping
* 🔍 Tree View Algorithms

---

# 🎯 Learning Outcomes

After completing this program you will understand:

✔ What the **Top View of a Binary Tree** is
✔ How **horizontal distance** works in tree problems
✔ How to use **BFS with a queue**
✔ How HashMap helps track nodes efficiently

These concepts are important for **Data Structures and Algorithms (DSA)** and **technical interviews**.

---

# 👨‍💻 Author

Developed as part of **Data Structures and Algorithms practice** 🚀
