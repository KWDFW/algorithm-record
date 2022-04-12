Day12

[146、 LRU缓存机制](https://leetcode-cn.com/problems/lru-cache/)

[题解](https://leetcode-solution.cn/solutionDetail?type=3&id=12&max_id=2)

#javascript #链表

1、利用map对象的性质，可以保存键值对，并记录先后顺序

2、每次get或put操作时，都把原来的key重新插入一遍，使关键字更新

## 代码
```javascript
LRUCache.prototype.get = function(key) {
    if(this.map.has(key)){//如果调用了就重新插入一个键值对，保持关键字的更新
        const temp=this.map.get(key)
        this.map.delete(key)
        this.map.set(key,temp)
        return temp
    }
    else return -1
};

/** 
 * @param {number} key 
 * @param {number} value
 * @return {void}
 */
LRUCache.prototype.put = function(key, value) {
    if(this.map.has(key)){//如果存在则重新插入键值对，保持关键字的更新
        this.map.delete(key)
    }
    this.map.set(key,value)
    if(this.map.size>this.capacity){
        this.map.delete(this.map.keys().next().value)//超过容量，就删除该关键字
    }
};
```
## 复杂度分析
时间复杂度：O(1)

空间复杂度：O(n)
