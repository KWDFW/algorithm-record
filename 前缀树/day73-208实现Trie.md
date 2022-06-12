Day73

[208、实现Trie](https://leetcode.cn/problems/implement-trie-prefix-tree/)

#javascript #前缀树
## 思路
1、构造前缀树

## 代码
```javascript
var Trie = function() {
  this.children = {};
};

/** 
 * @param {string} word
 * @return {void}
 */
Trie.prototype.insert = function(word) {
  let node = this.children;
  for (const ch of word) {
    if (!node[ch]) {
      node[ch] = {};
    }
    node = node[ch];
  }
  node.isEnd = true;
};

/** 
 * @param {string} word
 * @return {boolean}
 */
Trie.prototype.search = function(word) {
  let node = this.children;
  for (const ch of word) {
    if (!node[ch]) {
      return false;
    }
    node = node[ch];
  }
  return node.isEnd === true;
};

/** 
 * @param {string} prefix
 * @return {boolean}
 */
Trie.prototype.startsWith = function(prefix) {
  let node = this.children;
  for (const ch of prefix) {
    if (!node[ch]) {
      return false;
    }
    node = node[ch];
  }
  return true;
};

/**
 * Your Trie object will be instantiated and called as such:
 * var obj = new Trie()
 * obj.insert(word)
 * var param_2 = obj.search(word)
 * var param_3 = obj.startsWith(prefix)
 */
```
## 复杂度分析
时间复杂度：O(n)

空间复杂度：O(s)
