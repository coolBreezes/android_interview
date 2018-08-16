# RecyclerView

## 1、基本用法

1. setLayoutManager
   1. LinearLayoutManager
   2. GridLayoutManager
   3. StraggeredGridLayoutManager
2. RecyclerView.Adapter&lt;&gt;
   1. onCreateViewHolder
   2. onBindViewHolder
   3. getItemCount
   4. getItemViewType
   5. notifyItemInserted \(notifyItemRangeInserted\)
3. 设置分隔线

```text
//添加Android自带的分割线
recyclerView.addItemDecoration(new DividerItemDecoration(this,DividerItemDecoration.VERTICAL));
```

    4.性能优化

     1）、recyclerView.setHasFixedSize\(true\);





