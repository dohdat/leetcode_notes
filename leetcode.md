## DFS                   

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

## BFS

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


DFS:  Check if valid BST                                                                
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
## Graph traversal (2 directions)                   

```javascript
  let preMap = new Map();
  let visited = new Set();
 
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

## Binary Search                   
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

## Two Pointers                   
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
## Sliding Window                   
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

## Bellman Ford                   
**Time:** O(V * E), where V is the number of vertices and E is the number of edges.

**Space:** O(V + E)
```javascript
var networkDelayTime = function(times, n, k) {
  let arr = new Array(n + 1).fill(Infinity);
  arr[k] = 0;
  for (let i = 0; i <= n; i++) {
    let temp = arr.slice();
    for (let [source, target, cost] of times) {
      if (temp[source] === Infinity) continue;
      temp[target] = Math.min(temp[target], temp[source] + cost);
    }
    arr = temp;
  }
  arr.shift();
  let res = Math.max(...arr);
  return res === Infinity ? -1 : res;
};
```


## Dijkstra                   
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
 
  // Priority queue to store nodes based on distance, MaxPriorityQueue or MinPriorityQueue
  const priorityQueue = new PriorityQueue(
    (a, b) => distances[a] - distances[b]
  );
  priorityQueue.enqueue(k);
 
  while (!priorityQueue.isEmpty()) {
    const currentNode = priorityQueue.dequeue().element;
 
    if (graph.has(currentNode)) {
      for (const [nextNode, time] of graph.get(currentNode)) {
        const newDistance = distances[currentNode] + time;
        if (newDistance < distances[nextNode]) {
          distances[nextNode] = newDistance;
          priorityQueue.enqueue(nextNode);
        }
      }
    }
  }
 
  // Find the maximum distance in the distances array
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

## Backtrack (Permutations)                  
Time: O(n!) 

Space: O(n)
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
## Backtrack (Combinations)                  
Time: O(n!) 

Space: O(n)
```javascript
// Generate all possible combos.
const arr = ["cha", "r", "act", "ers"];
 
result: [
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
 const result = [];
 
 function backtrack(start, current) {
 if (start === arr.length) {
 result.push(current.join(''));
 return;
 }
 
 for (let i = start; i < arr.length; i++) {
 current.push(arr[i]);
 backtrack(i + 1, current);
 current.pop();
 }
 }
 
 backtrack(0, []);
 return result;
}
```

## Topology Sort                
**Time Complexity:** O(V + E)

**Space Complexity:** O(V + E)

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
