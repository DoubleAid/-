## 格式
```
 function getData() {
         $.ajax({
            url:'/',
            data:{'host':host_ip},
            type:'POST',
            async:false,
            dataType:'json',
            success:function(data) {
              myChart.setOption()
            },
            error:function (msg) {
                console.log(msg);
                alert('系统发生错误');
            }
        })
```

## 解析
