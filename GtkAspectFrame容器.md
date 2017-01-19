当你希望让用户可以改变元件尺寸，但是却想保持其比例，那么这个时候GtkAspectFrame 是非常有用的。比如说，你可以显示一个大图像的小预览。

# 构造函数
~~~
GtkAspectFrame ([string label = null [, double xalign = 0.5 [, double yalign = 0.5 [, double ratio = 1.0 [, bool obey_child = true]]]]]);  
~~~

使用构造函数创建带有参数的新的 GtkAspectFrame 的对象实例。

下面我们来通过一段测试代码演示一下，代码如下：
~~~
<?php       
if(!class_exists('gtk')){       
    die("php-gtk2 模块未安装 \r\n");  
}   
  
$label1=new GtkLabel('frame1');   
$label1->set_label("<b>Frame框架标题</b>");   
$label1->set_use_markup(true);   
$label1->set_alignment(0.5, 0.5);           
$label1->set_padding(0, 0);           
$label1->set_visible(true, false);   
  
$images1=GtkImage::new_from_file('big.jpg');   
  
// 创建GtkFrame   
$frame1 = new GtkAspectFrame('测试代码');   
$frame1->set_label_align(0,0.5);   
$frame1->add($images1);   
$frame1->set_label_widget($label1);   
$frame1->set_extension_events(Gdk::EXTENSION_EVENTS_CURSOR);   
$frame1->set_visible(true, false);   
  
// 创建窗口   
$wnd = new GtkWindow();   
$wnd->set_title('GtkAspectFrame 测试页面');   
$wnd->connect_simple('destroy', array('Gtk', 'main_quit'));   
$wnd->add($frame1);   
$wnd->show_all();   
Gtk::main();
~~~

程序运行效果如下图所示：
![](image/screenshot_1482324285375.png)