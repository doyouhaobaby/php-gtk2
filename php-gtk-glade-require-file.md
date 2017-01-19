首先是需要加载之前的 .glade 文件。 GladeXML 构造函数接受文件路径作为第一个参数， 所以我们需要做的是：

# 例 1. 加载 .glade 文件
~~~
<?php   
if(!class_exists('gtk')){   
	die("php-gtk2 模块未安装 \r\n");   
}   
  
// 加载glade文件，并且返回窗口实例   
$glade = new GladeXML('helloglade.glade');   
  
// 开始主循环   
Gtk::main();   
?>  
~~~
当运行这个脚本时，你会发现屏幕上显示出来有一个按钮的窗口， 但是除了关闭窗口不可以做其他任何事情。甚至窗口销毁了以后脚本仍然运行 —— 很明显缺少信号处理的连接，如图。

# 手工连接信号处理

下一步，只需要像我们已经知道的那样连接信号处理：针对元件对象调用 connect 或 connect_simple。获取对象只要使用 get_widget() 并作为参数传递元件名称（id）。 然后像往常一样的方式：

# 例 2. 获取并连接信号处理
~~~
<?php   
if(!class_exists('gtk')){   
	die("php-gtk2 模块未安装 \r\n");   
}   
  
// 加载glade文件，并且返回窗口实例   
$glade = new GladeXML('helloglade.glade');   
  
// 关闭窗口或右键关闭   
$window = $glade->get_widget('wndClose');   
$window->connect_simple('destroy', array('Gtk', 'main_quit'));   
  
// 按钮关闭   
$button = $glade->get_widget('btnClose');   
$button->connect_simple('clicked', 'onClickButton');   
  
function onClickButton() {   
      echo "按钮被点击了!\r\n";   
      Gtk::main_quit();   
}   
  
// 开始主循环   
Gtk::main();   
?>  
~~~

# 使用 Glade 连接信号处理
你可能已经注意到 .glade 文件中的 <signal> 标签—— 它使得在文件中直接定义信号处理成为了可能。我们需要做的就是通过调用 signal_autoconnect() 告诉 Glade 建立连接。

你可以定义普通的函数名作为处理方式，当事件发生时调用。 或者使用两个冒号分隔的类和静态方法，如Classname::methodName。

# 例 3. 使用 signal_autoconnect
~~~
<?php   
if(!class_exists('gtk')){   
	die("php-gtk2 模块未安装 \r\n");   
}   
  
// 加载glade文件，并且返回窗口实例   
$glade = new GladeXML('helloglade.glade');   
  
$glade->signal_autoconnect();   
  
function onClickButton() {   
      echo "按钮被点击了!\r\n";   
      Gtk::main_quit();   
}   
  
// 开始主循环   
Gtk::main();   
?>  
~~~

# 连接到对象方法 
仅仅连接到普通函数或静态方法不能满足真正的好程序员的需要。避免混乱的代码， 我们需要能够将信号连接到对象的方法上。
使用这个是非常简单的：仅仅需要将使用那个对象作为第一个参数的 signal_autoconnect_instance() 替换 signal_autoconnect() 即可：

# 例 4. 使用 signal_autoconnect_instance
~~~
<?php   
if(!class_exists('gtk')){   
	die("php-gtk2 模块未安装 \r\n");   
}   
  
// 加载glade文件，并且返回窗口实例   
$glade = new GladeXML('helloglade.glade');   
  
class MyClass {   
      function onClickButton() {   
            echo "MyClass->onClickButton!\r\n";   
            Gtk::main_quit();   
      }   
  
      function staticMethod() {   
             echo "MyClass::staticMethod()\r\n";   
      }   
}   
  
// 连接实例   
$myClassInstance = new MyClass();   
$glade->signal_autoconnect_instance($myClassInstance);   
  
// 主循环   
Gtk::main();   
?>
~~~