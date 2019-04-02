


```javascript
/**
 * Definition for a binary tree node.
 * function TreeNode(val) {
 *     this.val = val;
 *     this.left = this.right = null;
 * }
 */
/**
 * @param {TreeNode} root
 * @param {number} L
 * @param {number} R
 * @return {number}
 */
const rangeSumBST = (root, L, R) => {
    f = (x) => { 
        if (x == null) return 0; 
        if (x.hasOwnProperty('TreeNode')) return f(x["TreeNode"]); 
        return (x.val>=L && x.val <=R ? x.val : 0) + f(x.left) + f(x.right) 
    }
    return f(root)
}
```
