GtkVBox 容器被定义去垂直组织子元素到一列上，所有子元素都拥有相同的高度。它能够根据子元素的尺寸提供任何大的尺寸，子元素占用少于配置的空间，它们在各自的空间中默认垂直居中。

我们使用继承至GtkBox类的的packing方法将子元素添加至GtkHBox中，比如说pack_start()或者add()，将子元素添加至所有容器元件中。

GtkVBox和GtkHBox是一组可以比较的，它们的使用方法一致。

同时参考： **GtkHBox, GtkTable, GtkButtonBox, GtkBox, GtkContainer.**

# 构造函数
~~~
GtkVBox ([bool homogeneous = false [, int spacing = 0]]);  
~~~

参数 homogeneous是一个boolean值，它决定着容器中所有子元件是否应该根据最大元件的宽度排列。默认的行为（false）是为了保持各个元件各自的宽度不被改变。第二个参数，空间，定义着元件左边的空间的最低像素数。

程序演示效果可以见上一节的GtkHBox的教程。