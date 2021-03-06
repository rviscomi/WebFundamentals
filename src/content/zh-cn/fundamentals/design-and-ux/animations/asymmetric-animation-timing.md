project_path: /web/_project.yaml
book_path: /web/fundamentals/_book.yaml
description:打破对称可使项目产生对比和吸引力。了解何时对项目应用此方法以及如何应用。

{# wf_updated_on:2014-10-21 #}
{# wf_published_on:2014-08-08 #}

# 不对称的动画定时 {: .page-title }

{% include "web/_shared/contributors/paullewis.html" %}

不对称的动画定时可让您在表达个性的同时快速响应用户交互，从而提升用户体验。还能使感觉出现对比，使界面在视觉上更吸引人。

### TL;DR {: .hide-from-toc }
* 使用不对称的动画定时为作品添加个性和对比效果。
* 务必有利于用户交互；当响应点按或点击时采用较短的持续时间，其他情况则可以留出较长的持续时间。


与大多数动画“规则”一样，您应进行试验以找出适合您的应用的方法，但是涉及用户体验时，用户是最不耐烦的。经验法则是**始终快速响应用户交互**。也就是说，大多数时候用户操作是不对称的，因此动画也可以不对称。

例如，当用户进行点按以显示边栏导航时，您应当尽快显示此导航，持续时间约 100 毫秒。但是，当用户清除菜单时，您可以让视图动画离开得慢一点，即大约 300 毫秒。

相比之下，在显示模态视图时，一般是显示错误或一些其他关键消息。在这种情况下，要慢一点显示视图，同样大约为 300 毫秒，但是在进行清除（由用户触发）时，应非常迅速地完成。

那么，一般的经验法则为：

* 对于用户交互触发的 UI 动画，例如视图变换或显示元素，采用快速前奏（短持续时间）和慢速结尾（较长持续时间）。
* 对于由代码触发的 UI 动画，例如错误或模态视图，采用较慢前奏（较长持续时间）和快速结尾（短持续时间）。


{# wf_devsite_translation #}
