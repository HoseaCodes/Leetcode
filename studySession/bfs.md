# Breadth First Search

Start at the route node and search each node before going down to the children.

```js
class Node {
  constructor(val) {
    this.val = val;
    this.left = null;
    this.right = null;
  }
}

const a = new Node("a");
const b = new Node("b");
const c = new Node("c");
const d = new Node("d");
const e = new Node("e");
const f = new Node("f");

a.left = b;
a.right = c;
b.left = d;
b.right = e;
c.right = f;

//     a
//    / \
//   b   c
//  / \   \
// d   e   f

const bfs = (root) => {
  const queue = [root];
  while (queue.length > 0) {
    let currentNode = queue.shift();
    if (currenetNode.left !== null) queue.push(currentNode.left);
    if (currenetNode.right !== null) queue.push(currentNode.right);
  }
};
```

```js
const validBST = (root) => {
  return validate(root, null, null);

  function validate(root, low, high) {
    if (root == null) return true;
    if (
      (low !== null && root.val <= low) ||
      (high !== null && root.val >= high)
    )
      return false;
    return (
      validate(root.left, low, root.val) && validate(root.right, root.val, high)
    );
  }
};
// Time: O(N)
// Space: O(N)
```
