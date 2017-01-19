在大项目中，你可能有许多窗口定义在 .glade 文件中， 并且在加载 .glade 时全部被加载。这会使得 a) 你的程序启动变得缓慢。b) 立即显示所有的窗口，如果你没有在 Glade 中设置隐藏。 此外，你可能希望 signal_autoconnect_instance() 连接 .glade 文件的一部分到一个对象，然后连接其他的部分到另外的对象。

解决这个问题的方法是 GladeXML 构造函数的第二个参数： 仅仅传递将要作为根元件的元件 id ，那么只有这部分的 .glade 文件会被加载。

# 例 1. 部分加载 .glade 文件
~~~
<?php   
if(!class_exists('gtk')){       
    die("php-gtk2 模块未安装 \r\n");       
}      
  
// 加载glade文件，并且返回窗口实例   
$glade = new GladeXML('helloglade.glade', 'btnClose');   
$btn = $glade->get_widget('btnClose');   
$window = $glade->get_widget('wndClose');   

// 输出为NULL   
var_dump($window);   
?>  
~~~