GtkHScale 是一个在指定的范围值内水平滑动的元件。当它被使用的时候，这个元件有一些配置放出。可以查看 GtkScale查看细节信息。

# 构造函数
~~~
GtkHScale ([GtkAdjustment adjustment = null]);   
~~~

# 创建一个新的水平滑动元件
~~~
GtkHScale::new_with_range (double min, double max, double step);   
~~~

# 创建一个在一定范围值内滑动的水平滑动元件
最后我们以一个测试程序结束本节教程，代码如下：
~~~
<?php       
if(!class_exists('gtk')){       
    die("php-gtk2 模块未安装 \r\n");    
}   
  
$label1=new GtkLabel('控制和显示演示');   
$label2=new GtkLabel('(C)queryphp.com 技术支持');   
$scale1=GtkHScale::new_with_range (0,100,0.5);   
  
$vbox1=new GtkVBox();   
$vbox1->add($label1);   
$vbox1->add($scale1);   
$vbox1->add($label2);   
  
$window1=new GtkWindow();   
$oPixbuf=GdkPixbuf::new_from_file('big.jpg');// 为窗口创建背景   
list($oPixmap,)= $oPixbuf->render_pixmap_and_mask(255);   
$oStyle=$window1->get_style();   
$oStyle=$oStyle->copy();   
$oStyle->bg_pixmap[Gtk::STATE_NORMAL]=$oPixmap;   
$window1->set_style($oStyle);   
$window1->set_title('GtkHScale 演示');   
$window1->set_default_size(400,200);// 窗口大小   
$window1->add($vbox1);   
$window1->connect_simple('destroy',array('Gtk','main_quit'));   
$window1->show_all();   
Gtk::main();  
~~~

程序运行效果如下图：
![](image/screenshot_1482557758607.png)