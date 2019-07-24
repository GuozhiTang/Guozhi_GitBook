# d. Json Insertion

## 1. 给json添加新的字段

* Before: test = { name: "name", age: "12" }
* After: test = { name: "name", age: "12", id: "12345"}

```javascript
var test = { name: "name", age: "12" };
test.id = "12345";
```

## 2. 给json添加一组数据

* Before: json = { “name”: "caocao", "sex": "male" }
* After: newJson = { "name": "liubei", "sex": "male" }

```javascript
var json = [{ “name”: "caocao", "sex": "male" }];
var newJson = '{ "name": "liubei", "sex": "male" }';
json.push(JSON.parse(newJson));
```

