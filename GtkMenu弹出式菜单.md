GtkMenu 是一个菜单元件，通常是 GtkMenuBar或者 GtkMenuItem的子元件。

GtkMenu 是一个 GtkMenuShell，实现了一个下拉菜单组成的 GtkMenuItem 的对象。菜单可以通过激活一个 来自 GtkMenuBar或者其它的GtkMenu的GtkMenuItem而下拉出来。

因为GtkMenuItem可以包含很多的GtkMenu，它有可能创造无限多层次的嵌套菜单。

# 构造函数
~~~
GtkMenu ();  
~~~

创建一个新的 GtkMenu实例。

程序运行效果可以查看《PHP-GTK容器：GtkMenuBar容器》这一节教程的效果。