```

    // 保存客户操作记录
    PageData operationRecordPd = new PageData();
    operationRecordPd.put("customerIds", new String[]{pd.getString("customerId")});


    insert into operation_record(customer_id,operation_type,operation_time,operation_user,operation_content)
 	values
 	<foreach collection="customerIds" item="customerId" separator=",">
 		(#{customerId}, #{operationType}, #{operationTime}, #{operationUser}, #{operationContent})
 	</foreach>
```



