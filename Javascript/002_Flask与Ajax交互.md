* [GET 方法](#get-方法)
* [AJAX 方法](#ajax-通用)
* [POST 方法](#post-方法)
* [getJSON 方法](#getjson-直接获取数据)
* [load 方法](#load-方法)


## GET 方法
GET 方法无法传递数据，只能从url处获取信息
1. 返回字符串
```
$.get("/mystring",function(data, status){
         alert("数据: " + data + "\n状态: " + status);
      });
      
@app.route('/mystring')
def mystring():
    return 'my string'
```
2. 返回 json 字典 数据
```
$.get("/mydict",function(data, status){
         alert("name: " + data.name + " age:" + data.age);
      });

@app.route('/mydict', methods=['GET', 'POST'])
def mydict():
    d = {'name': 'xmr', 'age': 18}
    return jsonify(d)
```
3. 返回 json 数据 数据
```
$.get("/mylist",function(data, status){
         alert("name: " + data[0]+ " age:" + data[1]);
      });

@app.route('/mylist')
def mylist():
    l = ['xmr', 18]
    return jsonify(l)
```
## AJAX 通用
<span id=“j2”></span>
Ajax 可以通过指定type的类型使用POST 和GET 方法，ajax也会通过是否上传数据判断GET或POST
```
$.ajax({url:"/mystring", data:{"mydata": "test"},success:function(data){
         alert(data);
      }});

@app.route('/mystring')
def mystring():
    return 'my string'
```
2. 上传和获取数据
```
$.ajax({url:"/dataFromAjax", data:{"mydata": "test data"},success:function(data){
         alert(data);
      }});

@app.route('/dataFromAjax')
def dataFromAjax():
    test = request.args.get('mydata')
    print(test)
    return 'dataFromAjax'
```
3. 获取 json 字典 数据
```
$.ajax({url:"/mydict", success:function(data){
         alert("name: " + data.name + " age:" + data.age);
      }});
      
@app.route('/mydict', methods=['GET', 'POST'])
def mydict():
    d = {'name': 'xmr', 'age': 18}
    return jsonify(d)
```
4. 获取json 数组 数据
```
 $.ajax({url:"/mylist", success:function(data){
         alert("name: " + data[0] + " age:" + data[1]);
      }});
      
@app.route('/mylist')
def mylist():
    l = ['xmr', 18]
    return jsonify(l)
```
## POST 方法
<span id=“j3”></span>
post 方法发送数据，获取数据
```
$.post("/mydict", function(data, status){
         alert("name: " + data.name + " age:" + data.age);

@app.route('/mydict', methods=['GET', 'POST'])
def mydict():
    d = {'name': 'xmr', 'age': 18}
    return jsonify(d)
```
## getJSON 直接获取数据
<span id=“j4”></span>
```
$.getJSON("/mydict",function(data){
            $.each(data, function(i, field){
                $("div").append(field + " ");
            });

@app.route('/mydict', methods=['GET', 'POST'])
def mydict():
    d = {'name': 'xmr', 'age': 18}
    return jsonify(d)
```
## load 方法
<span id=“j5”></span>
load() 方法通过 AJAX 请求从服务器加载数据，并把返回的数据放置到指定的元素中。
```
$("p").load("/mystring");
$("p").load("../static/test.txt");
```
