当编写 PHP-GTK 程序以及浏览 PHP-GTK 手册时，你会发现一些非常模糊的缩写。 这里将会逐一介绍它们的具体含义。

# PHP
PHP - PHP: Hypertext Processor - 是使用广泛的多用途脚本语言， 被设计用于 Web 开发，并可嵌入 HTML 中。

# GTK
GTK - the GIMP Tool Kit - 是设计用于创建图形用户界面的库。 它运行于多数类 UNIX 平台，Windows，以及支持 framebuffer 的设备。
GTK 库本身包含元件，也就是 GUI 组件，如 GtkButton 或者 GtkTextView。
GTK 依赖若干其他库的支持，如 GDK，Pango，ATK 和 GLib。 并全部整合打包于 GTK+ 中。

# GDK
GDK - the GIMP Drawing Kit - 是允许 GTK+ 支持多窗口系统的抽象层。 GDK 可在 X11，Windows，和 Linux framebuffer 设备上提供绘制和窗口系统工具。

# Pango
Pango 是国际化文本处理库。它围绕使用段落表达文本的 PangoLayout 对象。Pango 为 GtkTextView，GtkLabel， GtkEntry，以及其他 需要显示文本的 GTK+ 元件 提供文本处理引擎。

# ATK
ATK 是 Accessibility Tool Kit。它提供一系列的接口来支持图形用户界面交互 的易用性。例如，屏幕阅读器可以使用 ATK 获取屏幕上的文字并给盲人用户阅读。