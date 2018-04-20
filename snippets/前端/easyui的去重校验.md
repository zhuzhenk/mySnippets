```
<input type="text" name="providerCode" class="form-control easyui-textbox" data-options="required:true
<c:if test="${empty pd.id}">,validType:{'letterAndNum':'','length[4,4]':'',remote:['<%=basePath%>provider/hasPByCode.do','providerCode','代码已存在']}</c:if>
<c:if test="${not empty pd.id}">,validType:{'letterAndNum':'','length[4,4]':'',remote:['<%=basePath%>provider/hasPByCode.do?id=${pd.id}','providerCode','代码已存在']}</c:if>" 
value="${pd.providerCode}"/>
```

不喜欢easyui，乱七八糟的

