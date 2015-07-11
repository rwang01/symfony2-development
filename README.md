# 用Symfony2来开发网站 #

## 关于本教程 ##
这套教程翻译自法语在线教程[Développez votre site web avec le framework Symfony2](https://openclassrooms.com/courses/developpez-votre-site-web-avec-le-framework-symfony2)，作者为Alexandre Bacco，采用[Creative Commons许可证](http://creativecommons.org/licenses/by-nc-sa/2.0/)，由[SensioLabs](https://sensiolabs.com/)（这个SensioLabs就是推出Symfony的背后公司）和[OpenClassrooms](https://openclassrooms.com/)联合推出。

## 为什么翻译这套教程 ##
2005年，Symfony由法国公司SensioLabs推出后，以功能强大而著称，但伴随的代价也是较高的学习成本。国内曾经出国一本Symfony的书，但是那是symfony1.x版本（注意这里s是小写的）的。2011年推出的Symfony2相比较1有了较大改动，虽然仍然保留了一些核心的理念，但具体到代码层面，也是大为不同。但国内后来也没有出版过专门介绍Symfony2的书，大家学习Symfony2基本都是参考官方网站的[book](http://symfony.com/doc/current/book/index.html)和[cookbook](http://symfony.com/doc/current/cookbook/index.html)为主。

book和cookbook都是重要的参考资料，但在这以外，倘若可以有一本以实战为主，围绕一个具体例子具体展开的详细资料，那将是非常极好的补充。symfony1的时代有官方的jobeet教程，到了Symfony2官方就没有推出了。有国外的达人自己写了[jobeet的Symfony2版本](http://intelligentbee.com/blog/2013/08/07/symfony2-jobeet-day-1-starting-up-the-project)，github也有翻译成[中文的版本](https://github.com/happen-zhang/symfony2-jobeet-tutorial)，值得一读。

相比较jobeet，这套教程更为详尽（出版的纸质书达到416页）。它不要求读者有Symfony的基础（PHP的基础还是要的），甚至不需要有使用框架的经验。作者在写做时非常注意帮助初学者厘清各样的概念，我觉得是一本难得的可以独立使用来零基础自学Symfony2的好教程。虽然此书在线免费可读，但因为法语是小语种，此书的内容无法被广大的中国程序员们所接触到，所以我想自己把它翻译出来，希望可以对Symfony2在国内的推广起到一些帮助，提高大家的生产效率。

## 翻译时的原则 ##
- 因为反套这套教程不是为了正式出版，所以不会完全按照原文的语句一一翻译。我会尽量用自然的中文来表达原文的意思。
- 一些英文专有名词不翻译，比如bundle，service等，我觉得这样反而更好。
- 作者原文里的代码夹杂着英语单词和法语单词，我统一调整为英语代词，注释改为中文。
- 所有关于Windows下的专门内容不翻译。相比Windows，Linux环境对开发者友好得多。
- 本书有一章是关于在浏览器下运行Symfony2命令行的，个人觉得这个功能没什么太多用处。使用Linux的话已经可以很好地在本地或远程运行Symfony2的命令行了。因此不翻译此章。

## 注意事项 ##
- 本教程不需要有Symfony的使用经验，只要用过PHP即可。
- 如果是第一次接触Symfony2，原作者建议按照顺序读。
- 目前原作者的在线教程上对应的Symfony是2.6版本，我会根据Symfony2的版本演变更新代码（Symfony2.7, Symfony3...），也会根据官方推荐的最佳实践来调整原作者的内容。
- 限于我水平，如果大家发现什么问题，可以发我pull request。

## 目录 ##
1. 鸟瞰Symfony2
 1. Symfony2，一个PHP框架
 2. 你说什么？Symfony2?
 3. 用命令行来新建一个bundle
2. Symfony2基础
 1. 第一个用Symfony2实现的“Hello World!”
 2. 路由
 3. 控制器
 4. 模板引擎Twig
 5. 用Composer安装一个bundle
 6. 关于service的理论和实际创建
3. 用Doctrine2来管理数据库
 1. 业务逻辑层：entity
 2. 用Doctrine2来操作entity
 3. 用Doctrine2来获取entity
 4. 事件和Doctrine扩展
 5. 实战：总结下我们的代码
4. 用Symfony2来更上一层楼
 1. 管理表单
 2. 验证数据
 3. 安全和用户管理
 4. service的高级应用
 5. Symfony2下的事件管理
 6. 为网站提供多语言
5. 准备上线
 1. 转换请求里的参数成为entity
 2. 定制错误页面
 3. 用Assetic来管理CSS和JS
 4. 部署网站到生产环境
