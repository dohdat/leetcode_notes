
- [1. DFS](#1-dfs)
  - [1.1. DFS:  Check if valid BST](#11-dfs--check-if-valid-bst)
- [2. BFS](#2-bfs)
- [3. Graph traversal (2 directions)](#3-graph-traversal-2-directions)
- [4. Binary Search](#4-binary-search)
- [5. Two Pointers](#5-two-pointers)
- [6. Sliding Window](#6-sliding-window)
- [7. Bellman Ford](#7-bellman-ford)
- [8. Dijkstra](#8-dijkstra)
- [9. Backtrack (Permutations)](#9-backtrack-permutations)
- [10. Backtrack (Combinations)](#10-backtrack-combinations)
- [11. Topology Sort](#11-topology-sort)
- [12. Generate subarray](#12-generate-subarray)
- [13. Check if subsequence](#13-check-if-subsequence)
- [14. Number of islands](#14-number-of-islands)
- [15. Union Find](#15-union-find)
- [16. Trie](#16-trie)
- [17. Merge intervals](#17-merge-intervals)
- [18. Reverse linked list](#18-reverse-linked-list)
- [19. Topdown dp](#19-topdown-dp)
- [20. Useful methods](#20-useful-methods)
  - [20.1. HashMap sorting (keys or values)](#201-hashmap-sorting-keys-or-values)
  - [20.2. Create 2D Array](#202-create-2d-array)
  - [20.3. Split number into digits](#203-split-number-into-digits)


## 1. DFS                   

**Time:** O(V + E), where V is the number of vertices and E is the number of edges.

**Space:** O(V)

```javascript
let res = [];
function dfs(node) {
    if (!node) return false;
    node.left && dfs(node.left);
    res.push(node.val);
    node.right && dfs(node.right);
}
dfs(root);
return res;
```

### 1.1. DFS:  Check if valid BST                                                                
```javascript
var isValidBST = function(root) {
  function dfs(node, lower, upper) {
    if (!node) return true;
 
    if (lower < node.val && node.val < upper) {
      return dfs(node.left, lower, node.val) &&
        dfs(node.right, node.val, upper);
    } else {
      return false;
    }
  }
 
  let res = dfs(root, -Infinity, Infinity);
  return res;
};
```

## 2. BFS

**Time:** O(V + E), where V is the number of vertices and E is the number of edges.

**Space:** O(V) when all vertices are enqueued in the queue before reaching the target node.

```javascript
var levelOrder = function(root) {
    if(!root) return [];
    let q = [root];
    let res = [];
    while (q.length !== 0) {
        let temp = [];
        let len = q.length;
        for (let i = 0; i < len; i++) {
            let c = q.shift();
            temp.push(c.val);
            c.left && q.push(c.left);
            c.right && q.push(c.right);
        }
        res.push(temp);
    }
    return res;
};
```



## 3. Graph traversal (2 directions)                   

```javascript
  let preMap = new Map();
  let visited = new Set();

  // Adjacency matrix
  for (let [src, dst] of preq) {
    preMap.set(src, (preMap.get(src) || []).concat(dst));
    preMap.set(dst, (preMap.get(dst) || []).concat(src));
  }
 
  function dfs(node) {
    if (visited.has(node)) return;
    visited.add(node);
    let visiting = preMap.get(node);
 
    while (visiting && visiting.length > 0) {
      let c = visiting.shift();
      dfs(c);
    }
  }
 
  dfs(0);
  return visited.size;
```

## 4. Binary Search                   
**Time:** O(log n) 

**Space:** O(1)
```javascript
var search = function(nums, target) {
  let left = 0;
  let right = nums.length - 1;
  while (left <= right) {
    let mid = Math.floor((right + left) / 2);
    if (nums[mid] === target) {
      return mid;
    }
    if (nums[mid] > target) {
      right = mid - 1;
    } else {
      left = mid + 1;
    }
  }
  return -1;
};
```

## 5. Two Pointers                   
**Time:** O(n) for sorted arrays, O(n^2) for unsorted arrays

**Space:** O(1)
```javascript
var maxArea = function(height) {
  let left = 0;
  let right = height.length - 1;
  let max = 0;
  while (left <= right) {
    let curArea = Math.min(height[left], height[right]) * (right - left);
    if (height[left] <= height[right]) {
      left++;
    } else {
      right--;
    }
    max = Math.max(max, curArea);
  }
  return max;
};
```
## 6. Sliding Window                   
**Time:** O(n) for fixed-size windows, O(n^2) for variable-size windows

**Space:** O(n) 
```javascript
const getMaxSumOfFiveContiguousElements = (arr) => {
  let maxSum = -Infinity;
  let currSum;
 
  for (let left = 0; left <= arr.length - 5; left++) {
    currSum = 0;
 
    for (let right = left; right < left + 5; right++) {
      currSum += arr[right];
    }
 
    maxSum = Math.max(maxSum, currSum);
  }
 
  return maxSum;
};
```

## 7. Bellman Ford                   
**Time:** O(V * E), where V is the number of vertices and E is the number of edges.

**Space:** O(V + E)


```javascript
Input: times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
Output: 2
var networkDelayTime = function(times, n, k) {
  let arr = new Array(n + 1).fill(Infinity);
  arr[k] = 0;
  for (let i = 0; i <= n; i++) {
    let temp = arr.slice();
    for (let [source, target, cost] of times) {
      if (temp[source] === Infinity) continue;
      temp[target] = Math.min(temp[target], arr[source] + cost);
    }
    arr = temp;
  }
  arr.shift();
  let res = Math.max(...arr);
  return res === Infinity ? -1 : res;
};
```


## 8. Dijkstra                   
**Time:** O((V + E) log V), where V is the number of vertices and E is the number of edges.

**Space:** O(V + E)
```javascript
var networkDelayTime = function(times, n, k) {
  const graph = new Map();

  for (const [source, target, time] of times) {
    if (!graph.has(source)) {
      graph.set(source, []);
    }
    graph.get(source).push([target, time]);
  }

  // Initialize distance array with Infinity
  const distances = Array(n + 1).fill(Infinity);
  distances[k] = 0;

  // Regular queue to store nodes
  const queue = [];
  queue.push(k);

  while (queue.length > 0) {
    const curNode = queue.shift();

    if (graph.has(curNode)) {
      for (const [nextNode, time] of graph.get(curNode)) {
        const newDistance = distances[curNode] + time;
        if (newDistance < distances[nextNode]) {
          distances[nextNode] = newDistance;
          queue.push(nextNode);
        }
      }
    }
  }

  // Find the maximum distance in the distances array, excluding the first element
  // const distances = [Infinity, 0, 5, 10, 8];
  const maxDistance = Math.max(...distances.slice(1));

  // If any node is unreachable, return -1
  if (maxDistance === Infinity) {
    return -1;
  }

  return maxDistance;
};

```
--------------------------------------------------------------
**When to use Dijkstra vs Bellman:**

**Edge Weights:**

If all edge weights are all positive, Dijkstra's algorithm is a good choice.

If there are negative edge weights, or the possibility of negative cycles, Bellman-Ford is more suitable.

**Performance:**

Dijkstra's algorithm is generally faster for graphs with non-negative weights.

Bellman-Ford may be slower but is more versatile in handling negative weights.

## 9. Backtrack (Permutations)                  
**Time:** O(n!) 

**Space:** O(n)
```javascript
//Given an array nums of distinct integers, return all the possible permutations. You can return the answer in any order.
 
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

var permute = function(nums) {
  let res = [];
  let cur = new Set();
  function backtrack() {
    if (cur.size === nums.length) {
      res.push([...cur]);
      return;
    }
 
    for (let n of nums) {
      if (cur.has(n)) {
        continue;
      }
      cur.add(n);
      backtrack();
      cur.delete(n);
    }
  }
  backtrack();
  return res;
};
```
## 10. Backtrack (Combinations)                  
**Time:** O(n!) 

**Space:** O(n)
```javascript
// Generate all possible combos.
const arr = ["cha", "r", "act", "ers"];
 
res: [
 "characters",
 "charers",
 "chaacters",
 "chaers",
 "racters",
 "rers",
 "acters",
 "ers"
];

function generateCombinations(arr) {
    const res = [];

    function backtrack(start, cur) {
        if (start === arr.length) {
            res.push(cur.join(''));
            return;
        }
        for (let i = start; i < arr.length; i++) {
            cur.push(arr[i]);
            backtrack(i + 1, cur);
            cur.pop();
        }
    }
    backtrack(0, []);
    return res;
}
```

## 11. Topology Sort                
**Time:** O(V + E)

**Space:** O(V + E)

```javascript
Input: numCourses = 2, prerequisites = [[1,0],[0,1]]
Output: false
// Explanation: There are a total of 2 courses to take. 
// To take course 1 you should have finished course 0, and to take course 0 you should also have finished course 1. So it is impossible.

var canFinish = function(numCourses, prerequisites) {
  let preMap = new Map();
  let visited = new Set();
  for (let [crs, preq] of prerequisites) {
    preMap.set(crs, (preMap.get(crs) || []).concat(preq));
  }
  function dfs(node) {
    if (visited.has(node)) {
      return false;
    }
    visited.add(node);
    let visiting = preMap.get(node);
    while (visiting && visiting.length) {
      let c = visiting.shift();
      if (!dfs(c)) {
        return false;
      }
    }
    visited.delete(node);
    return true;
  }
 
  for (let i = 0; i < numCourses; i++) {
    if (!dfs(i)) {
      return false;
    }
  }
 
  return true;
};
```
## 12. Generate subarray               

```javascript
Input: arr = [1, 2, 3, 4]
Output: 
[
  [ 1 ],       [ 1, 2 ],
  [ 1, 2, 3 ], [ 1, 2, 3, 4 ],
  [ 2 ],       [ 2, 3 ],
  [ 2, 3, 4 ], [ 3 ],
  [ 3, 4 ],    [ 4 ]
]

function generateSubarrays(arr) {
  const subarrays = [];
 
  for (let i = 0; i < arr.length; i++) {
    for (let j = i; j < arr.length; j++) {
      const subarray = arr.slice(i, j + 1);
      subarrays.push(subarray);
    }
  }
 
  return subarrays;
}

```

## 13. Check if subsequence             

```javascript
// Example usage:
const stringA = "abcde";
const stringB = "ace";
 
console.log(isSubsequence(stringA, stringB)); // Output: true

function isSubsequence(a, b) {
    let i = 0;
    let j = 0;
 
    while (i < a.length && j < b.length) {
        if (a[i] === b[j]) {
            j++;
        }
        i++;
    }
 
    return j === b.length;
}

```

## 14. Number of islands          
**Time:** O(rows * cols)

**Space:** O(rows + cols)

```javascript
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1

var numIslands = function(grid) {
    let rows = grid.length;
    let cols = grid[0].length;
    let res = 0;
    function dfs(r, c) {
        if (r < 0 || c < 0 || r >= rows || c >= cols || !grid[r][c] || grid[r][c] === '0') {
            return;
        }
        grid[r][c] = '0';
        dfs(r - 1, c);
        dfs(r + 1, c);
        dfs(r, c - 1);
        dfs(r, c + 1);
    }
    for (let r = 0; r < rows; r++) {
        for (let c = 0; c < cols; c++) {
            if (grid[r][c] === '1') {
                res++;
                dfs(r, c);
            }
        }
    }
    return res;
};

```

## 15. Union Find         

**Examples**:

- Detect cycles in graphs
- How many connected components in a graph
- If 2 nodes are in the same connected component

```javascript
var validPath = function(n, edges, source, destination) {
  let parent = new Array(n);
  for (let i = 0; i < parent.length; i++) {
    parent[i] = i;
  }
 
  function find(a) {
    while (parent[a] !== a) {
      parent[a] = parent[parent[a]];
      a = parent[a];
    }
    return a;
  }
 
  function union(a, b) {
    const rootA = find(a);
    const rootB = find(b);
    if (rootA !== rootB) {
      parent[rootA] = rootB;
    }
  }
 
  for (let [a, b] of edges) {
    union(a, b);
  }
 
  return find(source) === find(destination);
};

```

## 16. Trie       


```javascript
class TrieNode {
  constructor() {
    this.children = {};
    this.isEndOfWord = false;
    this.words = [];
  }
}

class Trie {
  constructor() {
    this.root = new TrieNode();
  }

  insert(word) {
    let node = this.root;
    for (let char of word) {
      if (!node.children[char]) {
        node.children[char] = new TrieNode();
      }
      node = node.children[char];
      // Store the word in each node
      node.words.push(word);
      // Sort the words array to maintain lexicographical order
      node.words.sort();
      if (node.words.length > 3) {
        node.words.pop();
      }
    }
    node.isEndOfWord = true;
  }

  search(prefix) {
    let node = this.root;
    for (let char of prefix) {
      if (!node.children[char]) {
        return [];
      }
      node = node.children[char];
    }
    return node.words;
  }
}

var suggestedProducts = function(products, searchWord) {
  let res = [];
  // Sorting the products lexicographically
  products.sort();
  const trie = new Trie();
  for (let product of products) {
    trie.insert(product);
  }
  let prefix = "";
  for (let char of searchWord) {
    prefix += char;
    res.push(trie.search(prefix));
  }
  return res;
};


// Example usage:
Input: products = ["mobile","mouse","moneypot","monitor","mousepad"], searchWord = "mouse"
Output: [["mobile","moneypot","monitor"],["mobile","moneypot","monitor"],["mouse","mousepad"],["mouse","mousepad"],["mouse","mousepad"]]
// Explanation: products sorted lexicographically = ["mobile","moneypot","monitor","mouse","mousepad"].
// After typing m and mo all products match and we show user ["mobile","moneypot","monitor"].
// After typing mou, mous and mouse the system suggests ["mouse","mousepad"].


```

## 17. Merge intervals      

```javascript
var merge = function(intervals) {
    intervals.sort((a, b) => a[0] - b[0]);
    let prev = intervals[0];
    let res = [prev];
    for (let i = 0; i < intervals.length; i++) {
        let c = intervals[i];
        if (c[0] <= prev[1]) {
            prev[1] = Math.max(prev[1], c[1]);
        } else {
            res.push(c);
            prev = c;
        }
    }
    return res;
};

Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
// Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].

```

## 18. Reverse linked list        


```javascript
var reverseList = function(head) {
  let prev = null;
  let cur = head;
  while (cur) {
    [cur.next, prev, cur] = [prev, cur, cur.next];
  }
  return prev;
};

```

## 19. Topdown dp  
```javascript
Input: n = 3
Output: 3
// Explanation: There are three ways to climb to the top.
// 1. 1 step + 1 step + 1 step
// 2. 1 step + 2 steps
// 3. 2 steps + 1 step

var climbStairs = function(n) {
  let memo = new Map();
  function dfs(i) {
    if (i === n) return 1;
    if (i > n) return 0;
    if (memo.has(i)) {
      return memo.get(i);
    }
    const ways = dfs(i + 1) + dfs(i + 2);
    memo.set(i, ways);
    return ways;
  }
  return dfs(0);
};

```  

## 20. Useful methods
### 20.1. HashMap sorting (keys or values)     


```javascript
//Sort by keys
map1 = new Map([...map1.entries()].sort());

//Custom sort keys:
map1 = new Map([...map1.entries()].sort((a, b) => b[0] - a[0]));
 
//Custom sort values:
map1 = new Map([...map1.entries()].sort((a, b) => b[1] - a[1]));

```
### 20.2. Create 2D Array

```javascript
let matrix = Array.from(Array(rows), () => new Array(cols).fill(0));
```

### 20.3. Split number into digits
```javascript
let num = 12345;
let digits = [];

while (num != 0) {
    digits.push(num % 10);
    num = Math.trunc(num / 10);
}
digits.reverse();

console.log(digits); // Output: [1, 2, 3, 4, 5]

```
