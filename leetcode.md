## BFS:

Time: O(V + E), where V is the number of vertices and E is the number of edges.

Space: O(V) when all vertices are enqueued in the queue before reaching the target node.

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

## DFS:                   

Time: O(V + E), where V is the number of vertices and E is the number of edges.

Space: O(V)

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
## Graph traversal (2 directions):                   

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

## Binary Search:                   
Time: O(log n) 

Space: O(1)
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

## Binary Search:                   
Time: O(n) for sorted arrays, O(n^2) for unsorted arrays

Space: O(1)
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
## Sliding Window:                   
Time: O(n) for fixed-size windows, O(n^2) for variable-size windows

Space: O(n) 
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

## Bellman Ford:                   
Time: O(V * E), where V is the number of vertices and E is the number of edges.

Space: O(V + E)
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