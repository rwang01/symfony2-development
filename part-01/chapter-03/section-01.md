# 控制台的使用 #

首先，你需要知道以下这点：Symfony2里内置的命令并不是用浏览器通过web方式调用的，而是通过终端调用的。Symfony2包含了不少我们开发时经常要用到的命令行工具，那现在我们就来学如何使用控制台吧！

Symfony2命令行上的工具并不是给那些偏爱终端的极客们所准备的高深程序，它们只是为了给我们开发人员节省时间用的。你可以用它们生成一些反复出现的基础代码框架，也可以用它们来清空缓存，或是增加一个用户，或者做其它很多事情。不过不用被控制器吓着了。

打开终端，进入你安装Symfony2的根目录，在本教程中是`$HOME/Symfony`。我们要执行的文件是此路径下的`app/console`，所以输入以下命令。

```shell
$ php app/console
```

好的，你刚刚就已经执行了一个Symfony的命令了，不过这个命令其实也没做太多事情，我们只是小试牛刀一下。

> 如果这个命令执行失败并且终端提示你说`php`不是一个可执行程序，那你可能忘了把`php`加入到你的`PATH`环境变量里。

## Symfony2的终端可以做什么？ ##

好问题，我们应该经常这样多问问。回答很简单：让我们开发更省事！

通过控制台，我们可以做很多事情，比如建立一个数据库，清空缓存，添加或修改用户账户（不用借助phpMyAdmin），等等。不过本章里我们关注的是控制台的代码生成功能。

事情上，建立一个新的bundle，新的模型或者新的表单，它们基础性的代码都是一样的。控制台里的代码生成器要做的就是帮我们自动生成那些代码，可以给我们节省不少时间！

## Symfony2的终端怎么运作的？ ##

既然Symfony2是用PHP写的一个框架，它怎么会有控制台上的命令行程序呢？

你要知道PHP程序一般是通过浏览器调用网页来执行的，但同样也可以通过控制台来执行。事实上，从Symfony2自身来说，它全部是用PHP来写的，没有其它语言。如果你还不确定，那就打开`app/console`文件自己看看：

```php
#!/usr/bin/env php
<?php

set_time_limit(0);

require_once __DIR__.'/bootstrap.php.cache';
require_once __DIR__.'/AppKernel.php';

use Symfony\Bundle\FrameworkBundle\Console\Application;
use Symfony\Component\Console\Input\ArgvInput;
use Symfony\Component\Debug\Debug;

$input = new ArgvInput();
$env = $input->getParameterOption(array('--env', '-e'), getenv('SYMFONY_ENV') ?: 'dev');
$debug = getenv('SYMFONY_DEBUG') !== '0' && !$input->hasParameterOption(array('--no-debug', '')) && $env !== 'prod';

if ($debug) {
    Debug::enable();
}

$kernel = new AppKernel($env, $debug);
$application = new Application($kernel);
$application->run($input);
```

有没有注意到什么？这个文件里的代码和前端控制器里的很像哦。事实上，它们所做的事情几乎是一样的。它们都载入了同样的文件，也都加载了内核。但是对于命令行程序来说，它接收到的请求是来自控制台的，所以接下去执行的代码就不一样了。我们自己也可以写专为控制台执行而不通过浏览器执行的代码。从代码层面来说，没什么不一样，除了显示的结果里不再有HTML了。



