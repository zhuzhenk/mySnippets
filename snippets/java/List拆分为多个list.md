```
public static List<List<PageData>> createList(List<PageData> targe,int size) {
        List<List<PageData>> listArr = new ArrayList<List<PageData>>();  
        //获取被拆分的数组个数  
        int arrSize = (targe.size()+size-1)/size;
        List<PageData> newList = null ;
        for (int i = 0; i < arrSize; i++) {
            if((i+1)==arrSize){
                newList =targe.subList(i*size,targe.size());
            }else{
                newList =targe.subList(i*size,(i+1)*size);
            }
            listArr.add(newList);
        }
        return listArr;
    }
```



