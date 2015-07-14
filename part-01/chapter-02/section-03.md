# Symfony2和bundle #

## 划分成bundle ##

### bundle的概念 ###

从开始这么课起，你就遇到bundle这个术语好几次了，但它到底是什么意思呢？

简单来说，bundle就是组成你应用程序的基石。Symfony2用这个创新的概念来表达把一个功能所涉及的所有代码都放在同一个地方。比如我们假设你网站里有一个博客bundle，它应该包含控制器，模型，视图，CSS和JavaScript，等等，反正和博客功能直接相关的代码都在这个bundle里。

这样的组织方式让我们很自然地划分功能，从而把每个文件放在最适合的地方。如果一个JavaScript文件只是被博客bundle用到的话，那就把它放在这个bundle里。当然，在每一个bundle内部，我们仍然需要一个清晰的组织结构。我们稍后来看这一点。

### 一些bundle的例子 ###

为了更好地说明，我给你举几个bundle的例子，这些例子很常见：

- 用户bundle。它用来管理用户和组，也集成了用户的管理后台，还有那些我们早已习以为常的页面：用户注册表单页面，重置密码页面，等等。
- 博客bundle。它用来管理网站上一个博客。这个bundle可以用到上面那个用户bundle来链接到文章作者的个人信息页面和评论页面。
- 店铺bundle。它可以提供一些工具来管理商品和订单。

这些bundle都遵循一些一致的规则，所以它们可以和谐地工作。例如，一个论坛bundle和一个用户bundle应该要和睦共处：只有用户才能给论坛带来活力。:smirk:

### bundle的优势 ###

总有个问题要搞清楚：使用bundle有什么好处呢？

bundle除了可以让你根据功能来组织代码，也可以让你在应用程序之间重用bundle。这意味着你可以开发出一个功能，然后分享给其他开发人员，或是在你自己的其它项目里使用。当然，反过来也一样：你可以在你的项目里使用别人开发的bundle。

所以bundle的使用提供了无限的可能。想想看，网站上大量的常用功能你都不用自己开发了！你需要一个访客留言簿功能？可能有一个这样的bundle已经开发出来了。还需要一个博客？可能也有一个博客bundle可以拿来用了。

### Symfony社区开发的一些bundle ###

Symfony社区开发的几乎所有bundle都归类在了这个站点：http://knpbundles.com。那里有很多bundle，我给你列举几个：

- [FOSUserBundle](http://knpbundles.com/FriendsOfSymfony/FOSUserBundle) 这个bundle是用来管理你网站用户的。具体来说，它提供了一个User模型，一个完成各样基础功能的控制器（登陆，注册，退出，修改个人信息，等等），还有相关的视图。你只要安装这个bundle，然后稍微定制一下，你的网站就有一个会员空间的功能了！我们在后续的章节里会用到这个bundle。
- [FOSCommentBundle](http://knpbundles.com/FriendsOfSymfony/FOSCommentBundle) 这个bundle用来管理留言。具体来说，它提供了一个Comment模型（当然也有对应的控制器）来添加，修改和删除网站留言。当然，视图也提供了。装了这个bundle，你就可以在任意页面加上留言的功能了。
- [GravatarBundle](http://knpbundles.com/ornicar/GravatarBundle) 这个bundle可以用来管理[Gravatar](https://fr.gravatar.com/)web服务上的头像。具体来说，它给你的模板引擎提供了一个扩展，让你可以用一个函数调用轻松地显示来自Gravatar上的头像，很实用的。

我真心建议你在开发你自己的bundle前去http://knpbundles.com上看一下。如果上面已经有一个符合你要求的bundle，那你再重新发明轮子的话就太傻了。:smirk: 当然，我们先得学习如果安装第三方bundle。耐心点，我们会学到的！

## bundle的结构 ##

一个bundle应该包含一切：控制器，视图，模型，自定义的类等等，总而言之，为实现bundle功能而必须的一切代码都被包含在内。当然，这些代码被很好组织在各自的目录里，这样便于查找。下面的表是bundle里文件目录常见的组织方式：

| 目录                  | 说明          |
| :--------------------|:------------- |
| /Controller          | 控制器目录 |
| /DependencyInjection | 包含了该bundle的信息（比如自动加载配置信息）|
| /Entity              | 模型目录   |
| /Form                | 表单目录   |
| /Resources/config    | 包含一些配置文件（比如路由信息）|
| /Resources/public    | 包含这个bundle里可通过web公开访问的文件（比如CSS，JavaScript，图片等）|
| /Resources/views     | 包含了视图，比如twig的模板 |

> 译者注：表格第一列里的路径是相对于该bundle的路径，而不是Symfony2安装的根目录。另外根据官方的Symfony2最佳实践，如果这个bundle只是用于该项目而不会用来给其他人使用（通常命名为AppBundle，直接放在/src目录下），那么项目里用到的视图推荐直接放在Symfony2安装根目录下的`/app/Resources/views/`里。

这个结构其实很简单，好好记住吧。不过别以为它们是固定的，你可以建立你自己的目录来更好组织你的代码，只是上面这个约定俗成的结构可以让其他开发人员很快就弄懂你的bundle。当然，接下去我会带着你创建每个文件。:smirk:

## 本章小结 ##

- Symfony2主要有这几个目录：`app`，`src`，`vendor`，`web`。
- `src`目录包含你网站的源代码，你开发用的大部分时间都花在这个目录了。
- 有两种工作环境：
  + 生产环境是面向你的网站访客的。这个环境下的页面加载很快，也不会泻露错误信息给大家。
  + 开发环境是面向开发人员的，就是说是为你而设的。这个环境下页面加载比生产环境慢，但提供大量对开发有帮助的信息。
- Symfony2用MVC架构来很好地组织不同部分的源代码。
- bundle是你应用程序的基石：它包含了实现某个特定功能的一切。这样你就可以把网站的不同部分很好地组织起来。
- Symfony社区已经开发了大量的bundle。你自己去开发一个bundle之前最好查一下是不是已经有一个实现同样功能的bundle被开发出来了。
