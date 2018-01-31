```
$("#deleteButton").on('click', function(){
                var selectedRows = proDatagrid.datagrid('getChecked');
                if (selectedRows.length <= 0) {
                    $.messager.alert(INFO, '请勾选至少一条记录！');
                    return;
                }
                var ids = [];
                for (var i = 0; i < selectedRows.length; i++) {
                    ids.push(selectedRows[i].id);
                }
                $.messager.confirm(CONFIRM, '确认要删除吗？', function(r){
                    if(r){
                        $.gd.safeAjaxButtonClick($("#deleteButton"), {
                            url: '<%=basePath%>pro/delete',
                            type: "POST",
                            dataType: "json",
                            data: {"ids": ids.join(",")},
                            success: function(data) {
                                $.gd.messager.show(data, function(){
                                    if(data.code == 'success'){
                                        jSuccess("删除成功!");
                                        proDatagrid.datagrid('load');
                                    }else {
                                        $.messager.alert(INFO, data.message);
                                    }
                                });
                            }
                        });
                    }
                });
            });
//这种的，直接使用pd就可以接收到数据了            
            
            
            
```



