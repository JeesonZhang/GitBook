# http接口文档

## 描述

接口描述

## 请求

### 请求行
  
- 请求方法：`POST`
- 请求地址：`index`

### 请求头

- `Content-Type`: `application/json; charset=utf-8`
- `token`: `XXXXXXXXXXX`

### 请求参数

- 说明：
  |参数|名称|类型|必填|说明|
  |-|-|-|:-:|-|
  |name|名字|String|是|用户名|
  |page|页码|Number|否|不填为1|
  |hobby|爱好|List|否|不填为无|
  |score|分数|Map|否|不填为无|
  |...|...|...|...|...|

- 请求参数格式示例：

   ```json
   {
       "name": "Bob",
       "page": 1,
       "hobby": [
           "History",
           "Basketball",
           "Drawing"
       ],
       "score": {
           "Chinese": 78,
           "Math": 81,
           "English": 88
       }
   }
  ```

## 响应

### 响应行

### 响应头

- `Content-Type`: `application/json; charset=utf-8`

### 响应数据

- 说明

   |参数|名称|类型|必填|说明|
  |-|-|-|:-:|-|
  |name|名字|String|是|用户名|
  |page|页码|Number|否|不填为1|
  |hobby|爱好|List|否|不填为无|
  |score|分数|Map|否|不填为无|

- 示例

  ```json
     {
       "name": "Bob",
       "page": 1,
       "hobby": [
           "History",
           "Basketball",
           "Drawing"
       ],
       "score": {
           "Chinese": 78,
           "Math": 81,
           "English": 88
       }
   }
  ```
