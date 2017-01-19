GtkMessageDialog 是非常合适的消息对话框。它提供了一个带有消息类型（错误，问题等等）图标的附带一些消息的对话框。当然你也用不了多少步骤可以让Gtkdialog做到GtkDialog一样的效果，但是GtkMessageDialog还具有类型。

最简单的办法创建一个消息对话框的方法就是使用run()方法，尽管你可以在Gtk::DIALOG_MODAL参数传递。run方法将会自动创建dialog模态，然后等待用户响应它。run()返回一个整数值，这个返回值可以显示是按钮被点击还是对话框被关闭。

# run详细介绍
这个方法可以允许你分析出对话框发生的事。当你在GtkDialog调用这个方法的时候,GTK一直会堵塞直到对话框被销毁或者一个信号响应。

这是一个非常高高效的通过一个响应信号退出运行循环。如果你在循环刚刚开始的时候销毁了对话框，这个时候你的代码不能够知道你的对话框是否被销毁了。这个方法会在发生的响应的瞬间或者退出时返回一个响应ID。注意，当你得到响应的时候，你应该销毁了对话框。

# GtkMessageDialog的构造函数如下：
~~~
GtkMessageDialog ( GtkWindow parent , GtkDialogFlags flags , GtkMessage type , GtkButtonsType buttons , string message);  
~~~

构造函数的第一个参数为父级窗口，第一个参数为对话框类型（3种），第三个为消息类型，第四个为按钮类型，最后一个为消息。

# 对话框类型（GtkDialogFlags）

|  值  |  符号名称  |  描述  |
| --- | --- | --- |
|  1  |   Gtk::DIALOG_MODAL  |   设置对话框模态，set_modal可以做到  |
| 2   |  Gtk::DIALOG_DESTROY_WITH_PARENT  |  当父级被销毁的时候对话框也被销毁了，可以而通过set_destroy_with_parent()做到  |
|   4 |  Gtk::DIALOG_NO_SEPARATOR  |  是否在action area和对话框内容之间放置一个分割的横线  |

# 按钮类型（GtkButtonsType）
预设对话框的按钮类型。如果没有选择下面的按钮，Gtk::BUTTONS_NONE被毁设置，你可以通过add_buttons重新添加。

|  值  |  符号名称  |  描述  |
| --- | --- | --- |
|  0  |  Gtk::BUTTONS_NONE  |  没有设置按钮  |
| 1   |  Gtk::BUTTONS_OK  |  OK按钮  |
| 2   |  Gtk::BUTTONS_CLOSE  |  关闭按钮  |
|  3  |  Gtk::BUTTONS_CANCEL	  |  取消按钮  |
| 4  |  Gtk::BUTTONS_YES_NO  |  YES和NO按钮  |
|  5  |  Gtk::BUTTONS_OK_CANCEL  |  OK和CANCEL按  |

我们通过一个例子来描述一下，代码如下：
~~~
<?php       
if(!class_exists('gtk')){       
	die("OK和CANCEL按 \r\n");       
}   
  
$dialog = new GtkMessageDialog(null,0,Gtk::MESSAGE_QUESTION,Gtk::BUTTONS_YES_NO,'我会被覆盖');   
$dialog->set_markup('<b>你</b>喜欢<span foreground="red">这个世界吗</span>吗？ ');   
$dialog->set_title('你喜欢吗?');   
$answer = $dialog->run();   
$dialog->destroy();   
if($answer == Gtk::RESPONSE_YES) {   
    echo "Yes\r\n";   
} else if ($answer == Gtk::RESPONSE_NO) {   
    echo "Why not?\r\n";   
} else {   
    echo "意外?\r\n";   
}   
?>  
~~~
运行效果如下：
![](image/screenshot_1480955329595.png)