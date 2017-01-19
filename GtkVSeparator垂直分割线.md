GtkVSeparator 是一个垂直分隔线元件。它是一个包含一个带有一层阴影的一个垂直线，使得它看起来像是刻到窗口的元件。它用来分割水平布局的元件。

> 请注意：GtkVSeparator 不能够被添加到GtkMenus。

同样也可以参考：**GtkHSeparator。**

# 构造函数
~~~
GtkVSeparator ();  
~~~

创建一个新的 GtkVSeparator 对象，然后添加到它的父元件，它为一条垂直线。我们可以使用容器的大包方法(比如，pack_start())来组织垂直线周围的空隙。

程序运行效果可以查看《PHP-GTK控制和显示：GtkHSeparator水平分割线》这一节教程的效果。