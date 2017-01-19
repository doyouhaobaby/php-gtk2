GtkHPaned 是一个由两个水平分割的窗格的容器。两个窗格之间的部分通过一个可拖动的句柄是可以调整的。

# 构造函数
~~~
GtkHPaned ();  
~~~

创建一个新的窗格。

我们最后一个测试代码结束本教程，代码如下：
~~~
<?php       
if(!class_exists('gtk')){       
    die("php-gtk2 模块未安装 \r\n");       
}   
  
$vpane = new GtkHPaned();   
$vpane->set_border_width(5);   
  
$left = new GtkFrame('左边标题');   
$left->add(new GtkLabel('左部分'));   
$left->set_shadow_type(Gtk::SHADOW_IN);   
$vpane->add1($left);   
  
$right = new GtkFrame('右边标题');   
$right->add(new GtkLabel('右部分'));   
$right->set_shadow_type(Gtk::SHADOW_IN);   
$vpane->add2($right);   
  
// 创建GtkWindow窗口   
$wnd = new GtkWindow();   
$wnd->set_title('GtkHPaned 演示程序');   
$wnd->set_default_size(300,-1);   
$wnd->connect_simple('destroy', array('Gtk', 'main_quit'));   
$wnd->add($vpane);   
$wnd->show_all();   
Gtk::main();  
~~~

程序运行效果如下图：
![](image/screenshot_1482325668882.png)