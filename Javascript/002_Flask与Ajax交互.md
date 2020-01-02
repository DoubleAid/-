* [GET 方法](#get-方法)
* [AJAX 方法](#ajax-通用)
* [POST 方法](#post-方法)
* [getJSON 方法](#getjson-直接获取数据)
* [load 方法](#load-方法)
返回数据方式参考[GET 方法](#get-方法)
****

## GET 方法
GET 方法无法传递数据，只能从url处获取信息
上传数据方式为 http://abc.com/search/search?tag=all&keyWords=%E7%A6%BB%E8%81%8C&lc=cn&type=next#NewKeyWords=%E7%A6%BB%E8%81%8C
get 获取表单信息 使用的是 request.args.get() 方法
```
$.get("/mystring",function(data, status){
         alert("数据: " + data + "\n状态: " + status);
      });
      
@app.route('/mystring')
def mystring():
    # 获取数据
    num = request.args.get("num")
    if num == 1:
        # 返回字符串
        return 'my string'
    elif num == 2:
        # 返回 数组 数据
        mlist = ["are","you","ok"]
        return jsonify(mlist)
    else:
        # 返回 字典 数据
        mdict = {1:"are",2:"you",3:"ok"}
        return jsonify(mdict)
```
## AJAX 通用
使用 post 方法时，获取数据使用request.form.get(); 使用 get 方法时，获取数据使用request.args.get() 
<span id=“j2”></span>
Ajax 可以通过指定type的类型使用POST 和GET 方法，ajax也会通过是否上传数据判断GET或POST
1. get 方法获取数据
```
$.ajax({url:"/mystring",success:function(data){
         alert(data);
      }});

@app.route('/mystring')
def mystring():
    print(request.args.get("a"))
    return 'my string'
```
2. post 上传和获取数据
```
$.ajax({url:"/dataFromAjax", data:{"mydata": "test data"},type:'POST',success:function(data){
         alert(data);
      }});

@app.route('/dataFromAjax')
def dataFromAjax():
    test = request.form.get('mydata')
    print(test)
    return 'dataFromAjax'
```
## POST 方法
使用 post 方法时，获取数据使用request.form.get()
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
