```
select provider_code,provider_name,level,substring(provider_code,1,level*3-2) parent_code,
        (create_time &gt; concat(date_sub(curdate(),interval 1 day),' 16:30:00') and create_time &lt;= concat(curdate(),' 16:30:00')) as is_new
        from provider
        where provider_code != 'none'
        and create_time &lt;= concat(curdate(),' 16:30:00')
        order by level asc,provider_code asc
```



