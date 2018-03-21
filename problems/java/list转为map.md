```
list<PageData> -> Map<String,Map<String,List<PageData>>>
//这一部分使因为levelOneClassifyText和levelTwoClassifyText都是用逗号分隔的字符串，
//我需要将他们分组，所以必须将每个组合全部都列出来，
List<PageData> allSpiltedList = new ArrayList<>();
list.stream().forEach(e -> {
    String[] fenlei1Array = e.getString("levelOneClassifyText").split(",");
    String[] fenlei2Array = e.getString("levelTwoClassifyText").split(",");
    for (String s1 : fenlei1Array) {
        for (String s2 : fenlei2Array) {
            PageData pd = new PageData();
            pd.putAll(e);
            pd.put("level1",s1);
            pd.put("level2",s2);
            allSpiltedList.add(pd);
        }
    }
});
//把数据做下分类处理，只要就是list2Map这个方法
Map<String,List<PageData>> map = CommonUtil.list2Map(allSpiltedList,"level1");
Map<String,Map<String,List<PageData>>> result = new HashMap<>();
for (Map.Entry<String,List<PageData>> entry : map.entrySet()) {
    result.put(entry.getKey(),CommonUtil.list2Map(entry.getValue(),"level2"));
}
```

```
//list-map
public static Map<String,List<PageData>> list2Map (List list, String classify){
    return (Map<String,List<PageData>>) list.stream().collect(Collectors.groupingBy(e -> ((PageData) e).getString(classify)));

}
嗯
```



