在 RecyclerView 中使用：

...
public void onBindViewHolder(VH holder, int position) {
    ....
    
    /**
     * item.getText()：    显示的文本
     * item.isExpanded()： 保存的是当前行是否是展开状态
     */
    tvContent.setText(item.getText(), item.isExpanded(), new ExpandTextView.Callback() {
            @Override
            public void onExpand() {
                // 展开状态，比如：显示“收起”按钮
            }

            @Override
            public void onCollapse() {
                // 收缩状态，比如：显示“全文”按钮
            }

            @Override
            public void onLoss() {
                // 不满足展开的条件，比如：隐藏“全文”按钮
            }
        });
    }
    tvContent.setOnClickListener(new View.OnClickListener() {
        @Override
        public void onClick(View v) {
            // 保存当前行的状态
            item.setExpanded(!item.setExpanded());
            // 切换状态
            tvContent.setChanged(item.isExpanded());
        }
    });
}
