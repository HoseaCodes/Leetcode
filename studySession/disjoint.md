# Disjoint Set or Union-Find

Disjoint sets are to address the connectivity between the components of a network.

## Quick Find of a Disjoint

```js
class QuickFind {
  constructor(size) {
    this.disjointSet = [];

    for (let i = 0; i < size; i++) this.disjointSet[i] = i;
  }
  find(x) {
    return this.disjointSet[x];
  }

  connected = (x, y) => {
    return this.find(x) === this.find(y);
  };

  union = (x, y) => {
    const rootX = this.find(x);
    const rootY = this.find(y);
    if (rootX !== rootY) {
      this.disjointSet.forEach((value, index) => {
        if (value === rootY) {
          this.disjointSet[index] = rootX;
        }
      });
    }
  };
}

// class UnionFind {
//   constructor(size) {
//     this.parent = new Array.from({ length: size }, (_, i) => i);
//     this.count = new Array(size).fill(1);
//   }

//   find(node) {
//     if (this.parent[node] != node)
//       this.parent[node] = this.find(this.parent[node]);
//     return this.parent[node];
//   }

//   union(nodeX, nodeY) {
//     const rootX = this.find(nodeX),
//       rootY = this.find(nodeY);
//     if (rootX == rootY) return;

//     if (this.count[rootX] < this.count[rootY]) {
//       this.parent[rootX] = rootY;
//       this.count[rootY] += this.count[rootX];
//     } else {
//       this.parent[rootY] = rootX;
//       this.count[rootX] += this.count[rootY];
//     }
//   }
// }
```

### Time Complexity

| Union-find Constructor | Find | Union | Connected |
| ---------------------- | ---- | ----- | --------- |
| Time Complexity        | O(1) | O(N)  | O(1)      |

---

## Quick Union of a Disjoint

```js
class QuickUnion {
  constructor(size) {
    this.disjointSet = [];

    for (let i = 0; i < size; i++) this.disjointSet[i] = i;
  }

  find(x) {
    while (x !== this.disjointSet[x]) {
      x = this.disjointSet[x];
    }
    return x;
  }

  connected = (x, y) => {
    return this.find(x) === find(y);
  };

  union = (x, y) => {
    const rootX = this.find(x);
    const rootY = this.find(y);
    if (rootX !== rootY) this.disjointSet[rootY] = rootX;
  };
}
```

### Time Complexity

| Union-find Constructor | Find | Union | Connected |
| ---------------------- | ---- | ----- | --------- |
| Time Complexity        | O(N) | O(N)  | O(N)      |

---
