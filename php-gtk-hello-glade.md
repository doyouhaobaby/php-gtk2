本指南将介绍如何在 PHP-Gtk 2 应用中使用 .glade 文件的基础知识。

# 1): 介绍
Glade3 是用户界面设计器，允许你用鼠标创建 Gtk 2 应用而不需要编写程序。 工作成果保存在 .glade 文件中， 并且可以非常简单地加载到你的 PHP-Gtk 2 应用中。

使用 Glade 创建用户界面可以节约许多时间，特别是在大型项目中可以分工合作： 界面设计人员使用 Glade设计用户界面（可以不需要了解程序的任何内容） 而你可以专注编写程序而不是关系界面上某部分的易用性。

我们精练了 Glade 的使用方法，而不是设计繁琐的界面。 这样，用于演示的 .glade 会相当简单：窗口上面有一个按钮。
窗口的名字（id）是 wndClose， 同时按钮的名字是 btnClose。

# 2)：准备 helloglade.glade 文件
~~~
<?xml version="1.0" encoding="UTF-8" standalone="no"?>   
<!DOCTYPE glade-interface SYSTEM "glade-2.0.dtd">   
<!--*- mode: xml -*-->   
<glade-interface>   
  <widget class="GtkWindow" id="wndClose">   
    <property name="visible">True</property>   
    <property name="title" translatable="yes">点击关掉我</property>   
    <signal name="destroy" handler="gtk::main_quit"/>   
    <child>   
      <widget class="GtkButton" id="btnClose">   
        <property name="visible">True</property>   
        <property name="can_focus">True</property>   
        <property name="label">gtk-close</property>   
        <property name="use_stock">True</property>   
        <property name="response_id">0</property>   
        <signal name="clicked" handler="onClickButton"/>   
      </widget>   
    </child>   
  </widget>   
</glade-interface>  
~~~