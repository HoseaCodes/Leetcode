# Depth First Search DFS

Approach 1 - Recursive
Check each node that it is connected to all the way down the the node or null. If the node is not found it goes back to the top then check the next node to it's deepest depth. It will continue this pattern until the node is found.

```js
// pre-order traversal
const dfs = (root) => {
  // the tree is empty
  if (root == null) return;
  console.log(root.val);
  dfs(root.left);
  dfs(root.right);
};
// self, left, right

// post-order traversal
const dfs = (root) => {
  // the tree is empty
  if (root == null) return;

  dfs(root.left);
  dfs(root.right);
  console.log(root.val);
};
// left, right, self

// in-order traversal
const dfs = (root) => {
  // the tree is empty
  if (root == null) return;

  dfs(root.left);
  console.log(root.val);
  dfs(root.right);
};
// left, self, right
```

```js
/*
Input: tree = [7,4,3,null,null,6,19], target = 3
Output: 3
Explanation: In all examples the original and cloned trees are shown. The target node is a green node from the original tree. The answer is the yellow node from the cloned tree.
*/
var getTargetCopy = function (original, cloned, target) {
  function traverse(originalNode, clonedNode) {
    if (!originalNode) return;
    if (originalNode === target) return clonedNode;
    return (
      traverse(originalNode.left, clonedNode.left) ||
      traverse(originalNode.right, clonedNode.right)
    );
  }
  return traverse(original, cloned);
};
// Time = O(V+E) or O(N) - Linear
// O(V+E) == O(Nodes + Edges)
```

Approach 2
Check each node that it is connected to all the way down the the node or null. When you find a node place the node and its childern into a stack. Once you have search the childern you can remove them from the stack when they have not childern.

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

const dfs = (root) => {
  const stack = [root];
  while (stack.length > 0) {
    const currentNode = stack.pop();
    if (currentNode.right !== null) stack.push(currentNode.right);
    if (currentNode.left !== null) stack.push(currentNode.left);
  }
};

// Time = O(n)
// Space = O(n)
```

## Reference

- [Coderbyte](https://www.youtube.com/watch?v=fPz40W9mfCg)
