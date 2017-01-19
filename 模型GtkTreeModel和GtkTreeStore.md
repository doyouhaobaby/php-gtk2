GtkTreeModel 是GtkTreeView的模型接口定义部分。应用程序可以定义自己的模型，但是GtkTreeView提供了两个常用的方面：GtkListStore线性列表和GtkTreeStore层次树。对于GtkTreeView我们要作如下的声明，只有极少的应用程序才需要所有的，一般来说它们需要使用右边的（也就是第二个GtkTreeStore）。因此，这里我们只会有少量地关于GtkListStore的表述。

第一步是使用GtkTreeView，然后，创建一个GtkTreeStore去保持你的数据。模型包含一些行，而且同时每行包含相同的列。每一个列中单元包含相同的的数据类型。当模型被创建的时候这些列就被定义了，尽管如此，如果必要它们还是稍后修改。

# 例 1. Model例子
~~~
$model = new GtkTreeStore(GObject::TYPE_PHP_VALUE, GObject::TYPE_STRING);
~~~

这里我们创建了一个两列的GtkTreeStore。第一个列包含一个PHP变量（或者其它类型），第二个为字符串。这里有不同类型的变量，你可以查看GObject 枚举类型。我们使用第一个列来存放一个包含一个文件夹的所有信息，第二个列显示它的名字。

GtkTreeStore的参数类型可以为：
* GObject::TYPE_STRING
* GObject::TYPE_LONG
* GObject::TYPE_DOUBLE
* GObject::TYPE_INVALID
* GObject::TYPE_NONE
* GObject::TYPE_INTERFACE
* GObject::TYPE_CHAR
* GObject::TYPE_BOOLEAN
* GObject::TYPE_ENUM
* GObject::TYPE_FLAGS
* GObject::TYPE_POINTER
* GObject::TYPE_BOXED
* GObject::TYPE_PARAM
* GObject::TYPE_OBJECT
* GObject::TYPE_PHP_VALUE

至于列的定义顺序是没有关系。大家所知道的GtkTreeStore的顺序并不影响展示给用户的样子。甚至没有必要给用户显示所有的列。我们可以通过多种方法将节点插入到GtkTreeStore中。我更倾向于使用get_tree_store_insert_before函数，它被当做PHP中的insert_before函数。
，
# 例 2. 创建行
~~~
$folder = new_folder();   
$iter = $model->insert_before(null, null);   
$model->set($iter, 0, $folder);   
$model->set($iter, 1, $folder['name']);  
~~~
上面的代码，首先插入一个空的行道模型，接着为行的单元格插入值。

一个GtkTreeModel 可以让程序员通过不同的方法将创建行。这里我们可以看出，一个GtkTreeIter对象实质上扮演着行上的一个点。我们接着可以使用这个点，加入一个列数量，然后指向单元格。

GtkTreeIter对象同时也被用作insert_before的参数，去定义新节点的父节点，它的兄弟节点将会紧跟新的节点。如果父节点为NULL，就像上面的例子中所显示的一样，新的节点将会被添加至顶级，如果兄弟节点为NULL，那么这个时候新的节点就成为了父节点的的最后一个子节点。

GtkTreeIter对象也许是临时的，也许随着树添加或者删除节点而改变成为无效。存放它们也许是一个错误的想法。

你还可以移除行（gtk_tree_store_remove 或者 $model->remove()）。至于其它操作，大家可以参考PHP-GTK 2相关API文档。