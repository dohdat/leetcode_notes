
## 1. Binary Search                   
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

## 2. DFS                   

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

### 2.1. DFS:  Check if valid BST                                                                
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

## 3. BFS

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

## 4. Two Pointers                   
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

## 5. Sliding Window                   
**Time:** O(n) for fixed-size windows, O(n^2) for variable-size windows

**Space:** O(n) 
```javascript
let getMaxSumOfFiveContiguousElements = (arr) => {
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

## 6. Graph traversal (2 directions)                   

```javascript
var minScore = function(n, roads) {
  let visited = new Set();
  const preMap = new Map();

  for (const [source, target, time] of roads) {
    if (!preMap.has(source)) {
      preMap.set(source, []);
    }
    if (!preMap.has(target)) {
      preMap.set(target, []);
    }
    preMap.get(source).push([target, time]);
    preMap.get(target).push([source, time]);
  }

  let min = Infinity;

  function dfs(node) {
    visited.add(node);
    const neighbors = preMap.get(node) || [];
    for (const [nei, dis] of neighbors) {
      min = Math.min(min, dis);
      if (visited.has(nei)) {
        continue;
      }
      dfs(nei);
    }
  }

  dfs(1);
  return min;
};
```

## 7. Backtrack (Permutations)                  
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
## 8. Backtrack (Combinations)                  
**Time:** O(n!) 

**Space:** O(n)
```javascript
// Generate all possible combos.
let arr = ["cha", "r", "act", "ers"];
 
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
    let res = [];

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


## 9. Generate subarray               

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
  let subarrays = [];
 
  for (let i = 0; i < arr.length; i++) {
    for (let j = i; j < arr.length; j++) {
      let subarray = arr.slice(i, j + 1);
      subarrays.push(subarray);
    }
  }
 
  return subarrays;
}

```

## 10. Check if subsequence             

```javascript
// Example usage:
let stringA = "abcde";
let stringB = "ace";
 
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

## 11. Number of islands          
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
  if (grid.length === 0) return 0;
  let rows = grid.length;
  let cols = grid[0].length;
  let res = 0;
  function isNotValid(r, c) {
    if (r < 0 || c < 0 || r >= rows || c >= cols || !grid[r][c] || grid[r][c] === "0") {
      return true;
    }
    return false;
  }

  function dfs(r, c) {
    if (isNotValid(r, c)) {
      return;
    }
    grid[r][c] = "0";
    dfs(r - 1, c);
    dfs(r + 1, c);
    dfs(r, c - 1);
    dfs(r, c + 1);
  }
  for (let r = 0; r < rows; r++) {
    for (let c = 0; c < cols; c++) {
      if (grid[r][c] === "1") {
        res++;
        dfs(r, c);
      }
    }
  }
  return res;
};


```

## 12. Union Find         

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
    let rootA = find(a);
    let rootB = find(b);
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

## 13. Trie       

```javascript
class TrieNode { 
	constructor() { 
		this.children = new Map(); 
		this.isEndOfWord = false; 
	} 
} 

class Trie { 
	constructor() { 
		this.root = new TrieNode(); 
	} 

	insert(word) { 
		let cur = this.root; 
		for (let i = 0; i < word.length; i++) { 
			const ch = word.charAt(i); 
			if (!cur.children.has(ch)) { 
				cur.children.set(ch, new TrieNode()); 
			} 
			cur = cur.children.get(ch); 
		} 
		cur.isEndOfWord = true; 
	} 

	search(word) { 
		let cur = this.root; 
		for (let i = 0; i < word.length; i++) { 
			const ch = word.charAt(i); 
			if (!cur.children.has(ch)) { 
				return false; 
			} 
			cur = cur.children.get(ch); 
		} 
		return cur.isEndOfWord; 
	} 
} 

const trie = new Trie(); 
trie.insert("hello"); 
trie.insert("world"); 
trie.insert("hi"); 

console.log(trie.search("hello")); // prints true 
console.log(trie.search("world")); // prints true 
console.log(trie.search("hi")); // prints true 
console.log(trie.search("hey")); // prints false 



```

## 14. Merge intervals      

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

## 15. Reverse linked list        


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

## 16. Topdown dp  
```javascript
Input: nums = [1,1,1,1,1], target = 3
Output: 5
Explanation: There are 5 ways to assign symbols to make the sum of nums be target 3.
-1 + 1 + 1 + 1 + 1 = 3
+1 - 1 + 1 + 1 + 1 = 3
+1 + 1 - 1 + 1 + 1 = 3
+1 + 1 + 1 - 1 + 1 = 3
+1 + 1 + 1 + 1 - 1 = 3

var findTargetSumWays = function(nums, target) {
  let memo = new Map();

  function backtrack(index, total) {
    if (index === nums.length) {
      return total === target ? 1 : 0;
    }

    let key = `${index},${total}`;
    if (memo.has(key)) {
      return memo.get(key);
    }

    let add = backtrack(index + 1, total + nums[index]);
    let subtract = backtrack(index + 1, total - nums[index]);

    memo.set(key, add + subtract);
    return add + subtract;
  }

  return backtrack(0, 0);
};

```  

## 17. Stack 
```javascript
var isValid = function(s) {
  const map = { "(": ")", "[": "]", "{": "}" };
  let stack = [];
  for (let i = 0; i < s.length; i++) {
    if (map[s[i]]) {
      stack.push(map[s[i]]);
    } else if (stack.pop() !== s[i]) {
      return false;
    }
  }
  return stack.length === 0;
};

Input: s = "()[]{}"
Output: true

```  
## 18. Topology Sort                
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

## 19. Bellman Ford (negative weights)                  
**Time:** O(V * E), where V is the number of vertices and E is the number of edges.

**Space:** O(V + E)


```javascript
Input: times = [[2,1,1],[2,3,1],[3,4,1]], n = 4, k = 2
Output: 2
var networkDelayTime = function(times, n, k) {
  let arr = new Array(n + 1).fill(Infinity);
  arr[k] = 0;
  for (let i = 0; i <= n; i++) {
    // Create a shallow copy
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


## 20. Dijkstra                   
**Time:** O((V + E) log V), where V is the number of vertices and E is the number of edges.

**Space:** O(V + E)
```javascript
var networkDelayTime = function(times, n, k) {
  let graph = new Map();

  for (let [source, target, time] of times) {
    if (!graph.has(source)) {
      graph.set(source, []);
    }
    graph.get(source).push([target, time]);
  }

  // Initialize distance array with Infinity
  let dst = Array(n + 1).fill(Infinity);
  dst[k] = 0;

  // Regular queue to store nodes
  let queue = [];
  queue.push(k);

  while (queue.length > 0) {
    let curNode = queue.shift();

    if (graph.has(curNode)) {
      for (let [nextNode, time] of graph.get(curNode)) {
        let newDistance = dst[curNode] + time;
        if (newDistance < dst[nextNode]) {
          dst[nextNode] = newDistance;
          queue.push(nextNode);
        }
      }
    }
  }

  // Find the maximum distance in the dst array, excluding the first element
  // let dst = [Infinity, 0, 5, 10, 8];
  let maxDistance = Math.max(...dst.slice(1));

  // If any node is unreachable, return -1
  if (maxDistance === Infinity) {
    return -1;
  }

  return maxDistance;
};

```

## 21. Useful methods
### 21.1. HashMap sorting (keys or values)     


```javascript
// Create a hashmap
const hashmap = nums.reduce((acc, val) => acc.set(val, (acc.get(val) || 0) + 1), new Map());

//Sort by keys
map1 = new Map([...map1.entries()].sort());

//Custom sort keys:
map1 = new Map([...map1.entries()].sort((a, b) => b[0] - a[0]));
 
//Custom sort values:
map1 = new Map([...map1.entries()].sort((a, b) => b[1] - a[1]));

```
### 21.2. Create 2D Array

```javascript
let matrix = Array.from(Array(rows), () => new Array(cols).fill(0));
```

### 21.3. Split number into digits
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

### 21.4. Filter
```javascript
const words = ['spray', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter((word) => word.length > 6);

console.log(result);
// Expected output: Array ["exuberant", "destruction", "present"]

```

### 21.5. MinQueue
```javascript
class MinQueue {
    constructor() {
        this.queue = [];
        this.minQueue = [];
    }

    enqueue(value) {
        this.queue.push(value);
        
        while (this.minQueue.length > 0 && this.minQueue[this.minQueue.length - 1] > value) {
            this.minQueue.pop();
        }
        this.minQueue.push(value);
    }

    dequeue() {
        if (this.queue.length === 0) {
            throw new Error("Queue is empty");
        }
        let removedValue = this.queue.shift();
        
        if (removedValue === this.minQueue[0]) {
            this.minQueue.shift();
        }
        
        return removedValue;
    }

    getMin() {
        if (this.minQueue.length === 0) {
            throw new Error("Queue is empty");
        }
        return this.minQueue[0];
    }
}

// Example usage:
let mq = new MinQueue();
mq.enqueue(3);
mq.enqueue(1);
mq.enqueue(2);
console.log(mq.getMin()); // Output: 1
mq.dequeue();
console.log(mq.getMin()); // Output: 1
mq.dequeue();
console.log(mq.getMin()); // Output: 2

```

### 21.6. Insert Intervals
```javascript

Example 1:

Input: intervals = [[1,3],[6,9]], newInterval = [2,5]
Output: [[1,5],[6,9]]
Example 2:

Input: intervals = [[1,2],[3,5],[6,7],[8,10],[12,16]], newInterval = [4,8]
Output: [[1,2],[3,10],[12,16]]
Explanation: Because the new interval [4,8] overlaps with [3,5],[6,7],[8,10].


var insert = function(intervals, newInterval) {
    intervals.push(newInterval);
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

```

### 21.6. Robinhood orders
```javascript

class Order {
    constructor(id, type, price, quantity) {
        this.id = id;
        this.type = type;  // 'buy' or 'sell'
        this.price = price;
        this.quantity = quantity;
        this.timestamp = Date.now();
    }
}

class OrderBook {
    constructor() {
        this.buyOrders = [];
        this.sellOrders = [];
    }

    addOrder(order) {
        if (order.type === 'buy') {
            this.buyOrders.push(order);
            this.buyOrders.sort((a, b) => b.price - a.price || a.timestamp - b.timestamp);
        } else {
            this.sellOrders.push(order);
            this.sellOrders.sort((a, b) => a.price - b.price || a.timestamp - b.timestamp);
        }
        this.matchOrders();
    }

    matchOrders() {
        while (this.buyOrders.length && this.sellOrders.length) {
            let buyOrder = this.buyOrders[0];
            let sellOrder = this.sellOrders[0];

            if (buyOrder.price >= sellOrder.price) {
                let quantityToMatch = Math.min(buyOrder.quantity, sellOrder.quantity);
                console.log(`Matched ${quantityToMatch} @ ${sellOrder.price}`);

                buyOrder.quantity -= quantityToMatch;
                sellOrder.quantity -= quantityToMatch;

                if (buyOrder.quantity === 0) {
                    this.buyOrders.shift();
                }
                if (sellOrder.quantity === 0) {
                    this.sellOrders.shift();
                }
            } else {
                break;
            }
        }
    }

    cancelOrder(id) {
        this.buyOrders = this.buyOrders.filter(order => order.id !== id);
        this.sellOrders = this.sellOrders.filter(order => order.id !== id);
    }
}

// Example Usage
let orderBook = new OrderBook();
orderBook.addOrder(new Order(1, 'buy', 100, 10));
orderBook.addOrder(new Order(2, 'sell', 90, 5));
orderBook.addOrder(new Order(3, 'sell', 100, 5));
orderBook.addOrder(new Order(4, 'buy', 105, 5));


```
