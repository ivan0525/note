### 数组下标法
遍历需要去重的数组，如果当前数组的某个元素是第一次出现，则存入新的数组，否则忽略掉。
```javascript
let unique = function (arr) {
  let temp = []
  arr.forEach((item, index) => {
    if (temp.indexOf(item) === -1) {
      temp.push(item)
    }
  })
  return temp
}
```

### ES6中的Set
```javascript
let unique = function (arr) {
  return [...new Set(arr)]
}
```

### 根据对象的键的不重复性
```javascript
let unique = function (arr) {
  let obj = {}
  arr.forEach(item => obj[item] = item)
  return Object.keys(obj) // 这里会导致类型被转换（原本是number型的，转成了string类型）
}
```

### ES6中的Map和Set联合使用
```javascript
let unique = function (arr) {
  const map = new Map()
  return arr.filter(item => !map.has(item) && map.set(item, 1))
}
```