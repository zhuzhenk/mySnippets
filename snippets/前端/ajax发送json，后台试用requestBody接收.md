```
$.ajax({
        type: 'post',
        url: '<%=basePath%>customerPool/saveCallStatus.do',
        contentType: "application/json; charset=utf-8",
        data:  JSON.stringify({
            customerId: $("#customerIdPool").val(),
            callStatus: $("#callStatus").combobox('getValue'),
            latestContactTime: $("#latestContactTime").datetimebox('getValue')
        }),
        dataType: "json",
        success: function (data) {
            $.gd.messager.show(data, function () {
                $('#myTab a:first').tab('show');
                setTimeout(function(){
                    $("#recordRegister").datagrid('reload');
                },1000);
            }, '操作成功！');
        }
    });
        
        
           */
    @RequestMapping(value = "/saveCallStatus")
    @ResponseBody
    public MessageCode saveCallStatus(@RequestBody PageData pd) {
        MessageCode msg = null;
        try {
```



