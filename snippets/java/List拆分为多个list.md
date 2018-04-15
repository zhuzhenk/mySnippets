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

```
分组数(targe.size()+size-1)/size; //i+1==arrSize 判断是否为最后一组，因为i是从零开始的，所以加一
循环队列有这么一个算法 rearAfter=（rear+1)%数组长度  rear元素移动一个元素之后的位置，保证不会超过数组长度，可以循环
//静态栈,数组尾是栈顶，
//动态栈 链表头部是栈顶

//静态队列，使用循环，使用rearAfter=（rear+1)%数组长度来确定位置，rear元素不存储元素
//动态队列，使用两个指针head和end来控制，列表头部是链表的头部
```

```
数组是连续存储线性结构
链表是离散存储线性结构
二叉树是非线性数据结构

```



