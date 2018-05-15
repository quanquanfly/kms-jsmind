## kmsjsmap
思维导图JS库，对hizzgdev大神的库进行二次封装，扩展右键菜单，包含拖拽节点等功能。


## 1.引入样式
```
<link rel="stylesheet" type="text/css" href="./dist/kmsjsmap.min.css">
```

## 2.引入JS库
```
<script type="text/javascript" src="./dist/kmsjsmap.min.js"></script>
```


## 调用示例
```
kmsjsmap.init({
    container: "jsmind_container",
    data: [
      { "id": "root", "isroot": true, "topic": "华北大魏有限公司"},
      { "id": "sub1", "parentid": "root", "topic": "君主", "badge": 20, "direction": "left" },
      { "id": "sub12", "parentid": "sub1", "topic": "曹操", "badge": 30 },
      { "id": "sub121", "parentid": "sub1", "topic": "曹丕", "badge": 44 },
      { "id": "sub122", "parentid": "sub1", "topic": "曹叡", "badge": 44 },
      { "id": "sub123", "parentid": "sub1", "topic": "曹芳", "badge": 44 },

      { "id": "sub2", "parentid": "root", "topic": "军师", "badge": 66, "direction": "right", "expanded":false },
      { "id": "sub21", "parentid": "sub2", "topic": "郭嘉", "badge": 233 },
      { "id": "sub22", "parentid": "sub2", "topic": "荀彧", "badge": 9 },
      { "id": "sub23", "parentid": "sub2", "topic": "司马懿", "badge": 7 },
      { "id": "sub24", "parentid": "sub2", "topic": "贾诩", "badge": 77 },

      { "id": "sub3", "parentid": "root", "topic": "大将", "badge": 45, "direction": "right", "expanded":false },
      { "id": "sub31", "parentid": "sub3", "topic": "典韦", "badge": 1 },
      { "id": "sub32", "parentid": "sub3", "topic": "夏侯惇", "badge": 2 },
      { "id": "sub33", "parentid": "sub3", "topic": "于禁", "badge": 3 },
      { "id": "sub34", "parentid": "sub3", "topic": "许褚", "badge": 4 }
    ],
    onSave: function(res) {
      console.log(res)
    },
    editable: true,
    onRelation(item) {
      console.log('当前选择中的是', item)
    }
  });
```

## API 说明

参数 | 类型 | 是否必填 | 说明
-----  | ---- | -------- | -----
container | String | 是  | 容器元素ID
data | Array(Object) | 否  | 初始数据
onSave | Function | 否 | 用户点击"保存思维导图"按钮的回调函数，返回当前的数据结构
editable | Boolean | 否 | 是否允许编辑
onRelation | Function | 否 | 点击右键菜单"关联"时的回调，返回当前操作节点的信息

## API - data 说明
参数 | 类型 | 是否必填 | 说明
-----  | ---- | -------- | -----
id | String | 是  | 当前节点的ID
parentid | String | 是 | 父节点的ID
topic | String | 是 | 当前节点的内容文字
direction | Boolean | 否 | 当前节点的方向，此数据仅在第一层节点上有效，目前仅支持 left 和 right[默认] 两种
badge | Number | 否 | 当前节点的右上角小图标，如不传或传入0则不显示
expanded | Boolean | 否 | 是否默认展开该节点