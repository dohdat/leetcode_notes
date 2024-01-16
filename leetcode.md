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
