# LRU Cache

## 🧠 Problem
Design a data structure that supports:

- `get(key)` → return value if exists, else -1  
- `put(key, value)` → insert/update key  

When capacity is full → remove the **Least Recently Used (LRU)** item.

---

## ⚙️ Approach — HashMap + Doubly Linked List

Use:

✅ HashMap → O(1) access to nodes  
✅ Doubly Linked List → maintain usage order  

### Idea
- Most recently used → move to front  
- Least recently used → at tail → remove  

---

## 🪜 Operations

### get(key)
1. If key not in map → return -1  
2. Move node to front  
3. Return value  

### put(key, value)
1. If key exists → update value + move to front  
2. Else create node  
3. If capacity exceeded → remove tail node  
4. Insert new node at front  

---

## 🧾 Code Skeleton

```cpp
class LRUCache {
    int cap;
    unordered_map<int, Node*> map;
    Node *head, *tail;

    void remove(Node* node);
    void insertFront(Node* node);

public:
    LRUCache(int capacity);

    int get(int key) {
        if (!map.count(key)) return -1;
        Node* node = map[key];
        remove(node);
        insertFront(node);
        return node->val;
    }

    void put(int key, int value) {
        if (map.count(key)) {
            Node* node = map[key];
            node->val = value;
            remove(node);
            insertFront(node);
        } else {
            if (map.size() == cap) {
                map.erase(tail->key);
                remove(tail);
            }
            Node* node = new Node(key, value);
            insertFront(node);
            map[key] = node;
        }
    }
};
