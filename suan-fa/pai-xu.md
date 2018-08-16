# 排序

## 冒泡



{% embed data="{\"url\":\"https://blog.csdn.net/u010853261/article/details/54891710\",\"type\":\"link\",\"title\":\"\[排序算法\]--冒泡排序的三种实现\(Java\) - CSDN博客\",\"description\":\"冒泡排序是非常好理解的，以从小到大排序为例，每一轮排序就找出未排序序列中最大值放在最后。 设数组的长度为N：  （1）比较前后相邻的二个数据，如果前面数据大于后面的数据，就将这二个数据交换。（2）这样对数组的第0个数据到N-1个数据进行一次遍历后，最大的一个数据就“沉”到数组第N-1个位置。（3）N=N-1，如果N不为0就重复前面二步，否则排序完成。以上就是冒泡排序的基本思想，按照这个定义很快就能写\",\"icon\":{\"type\":\"icon\",\"url\":\"https://csdnimg.cn/public/favicon.ico\",\"aspectRatio\":0}}" %}

### 第一种

```text
for(int i = 0; i < arr.length-1; i++)
    for(int j = 0; j < arr.length-1-i;j++)
```

### 第二种

```text

while(flag){
    flag = false;
    for(int j = 0; j < k; j++)
    ....
    
    k--
}
```

