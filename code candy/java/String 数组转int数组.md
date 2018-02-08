```
String ids = pd.get("ids", String.class);
if(StringUtils.isNotEmpty(ids)){
    int[] idArr = Arrays.stream(ids.split(",")).mapToInt(e -> Integer.parseInt(e)).toArray();
    
    //////////////////////
    update article
		set is_publish = 1,
			publish_time = #{publishTime}
		where id in
		<foreach collection="ids" item="id" open="(" separator="," close=")">
			#{id}
		</foreach>
		and is_publish = 0
```



