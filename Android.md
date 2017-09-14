---
title: 技术总结 - Android 篇
grammar_cjkRuby: true
---


1.如何将一个Activity设置成窗口的样式？
* 只需在清单文件里修改Activity的theme  android:theme="@android:style/Theme.Dialog"
* 修改Activity的styles的windowBackground，自定义一个drawable

2.横竖屏切换的时候Activity的生命周期变化情况？
* 不设置Activity的android:configChanges时，切屏会重新调用各个生命周期，切横屏时会执行一次，切竖屏时会执行两次
* 设置Activity的android:configChanges="orientation"时，切屏还是会重新调用各个生命周期，切横、竖屏时只会执行一次
* 设置Activity的android:configChanges="orientation|keyboardHidden"时，切屏不会重新调用各个生命周期，只会执行onConfigurationChanged方法

3.Activity的启动模式有几种，分别是什么，有什么区别？
* ==Standard== 标准模式，且是默认的启动模式，每次都新建一个实例对象
* ==SingleTop== 如果在任务栈顶发现了相同的实例则重用，否则新建并压入栈顶
* ==SingleTask== 如果在任务栈中发现了相同的实例，将其上面的任务终止并移除，重用该实例。否则新建实例并入栈
* ==SingleInstance== 允许不同应用，进程线程等共用一个实例，无论从何应用调用该实例都重用

4.ImageView的ScaleType有几种？它们的特点和区别是什么？
* ==matrix==(默认) 不改变原图的大小，从ImageView的左上角开始绘制原图，原图超过ImageView的部分做裁剪处理
* ==center== 保持原图的大小，显示在ImageView的中心。当原图的size大于ImageView的size，超过部分裁剪处理。
* ==centerCrop== 以填满ImageView为目的，将原图的中心对准ImageVIew的中心，等比例放大原图，直到填满ImageView为止（指的是ImageView的宽高都要填满），原图超过ImageView的部分做裁剪处理。
* ==centerInside== 以原图完全显示为目的，将图片的内容完整居中显示，通过按比例缩小原图的size宽（高）等于或小于ImageView的宽（高）。如果原图的size本身就小于ImageView的size，则原图的size不做任何处理，居中显示在ImageView。
* ==fitCenter== 把原图按比例扩大或缩小到ImageView的高度，居中显示
* ==fitEnd== 把原图按比例扩大（缩小）到ImageView的高度，显示在ImageView的右部分位置
* ==fitStart== 把原图按比例扩大（缩小）到ImageView的高度，显示在ImageVIew的左部分位置
* ==fitXY== 把原图按照指定的大小在ImageView中显示，拉伸显示图片，不保持原比例，填满ImageView

5.View的绘制流程
* View的绘制是由==ViewRoot==来负责的。每个应用程序窗口的DecorView都有一个与之关联的ViewRoot对象。这种关联的关系是由WindowManage来维护的。
* ==绘制的起点== ViewRootImpl的performTraversals()方法
* 三个阶段
  *  measure：判断是否需要重新计算view的大小，需要的话计算
  *  layout：判断是否需要重新计算view的位置，需要的话计算
  *  draw：判断是否需要重新绘制view，需要的话重新绘制

6.触摸事件的传递机制
*  Android事件分发是先传递到ViewGroup，再由ViewGroup传递到View的。
*  在ViewGroup中可以通过onInterceptTouchEvent方法对事件传递进行拦截，onInterceptTouchEvent方法返回true代表不允许事件继续向子View传递，返回false代表不对事件进行拦截，默认返回false。
*  子View中如果将传递的事件消费掉，ViewGroup中将无法接收到任何事件。

7.如何提高APP的性能？可以从布局、代码、内存、网络等方面描述一下
 * 布局
   * 减少绘制不可见的UI操作
   * 推荐使用==RelativeLayout==布局
   * 布局==层数==尽量少（扁平化）
   * 尽量简化布局
 * 代码
   * 使用==优化==过的数据集合（SparseArray、SparseBooleanArray、LongSparseArray）
   * 尽量避免使用==依赖注入==框架
   * 使用==ProGuard==简化代码
   * 谨慎使用==抽象==编程
   * 不使用==枚举==（所占内存是静态常量的两倍）
   * 节制的使用Service（推荐使用IntentService）
* 内存
  *  当界面不可见时释放内存
  *  内存紧张时释放内存资源
  *  避免在Bitmap上浪费内存
  *  知晓内存的开支情况（Java类大致占500字节，对象实例占12-16字节）
* 网络
  *   减少网络数据获取的频次
  *    无缝的==GZIP==来减少数据流量（请求更快）
  *   使用==SPDY==，共享同一个socket来处理同一服务器的所有网络请求
  *   如果SPDY不可用，则通过==连接池==来减少请求延时
  *   ==缓存==响应数据来减少重复的网络请求
  
7.多屏幕适配可以从哪些方面入手？
* 使用wrap_content、math_parent、weight
* 使用相对布局，禁用绝对布局
* 使用限定符
  * 使用尺寸限定符
  * 使用最小宽度限定符
  * 使用布局别名
  * 使用屏幕方向限定符
* 使用自动拉伸位图

8.说一说常见图片加载库的实现原理
* Glide 收到加载及显示资源的任务，创建Request并交由RequestManage管理，Request启动Engine去数据源获取资源（通过Fetcher），获取到后Transformation处理后交给Target

9.说一说常见网络请求库通常做了什么封装？
 *   无缝的==GZIP==来减少数据流量（请求更快）
 *   使用==SPDY==，共享同一个socket来处理同一服务器的所有网络请求
 *   如果SPDY不可用，则通过==连接池==来减少请求延时
 *   ==缓存==响应数据来减少重复的网络请求

10.Fragment和Activity的区别
* Activity是系统的四大组件之一，由ActivityManage管理，生命周期由系统控制
* Fragment是在3.0后引入的组件，由FragmentManage管理，可以由Activity自由控制，引入或者删除，更方便
* FragmentManage和ActivityManage都有缓存机制，getFragmentByTag或者ById查看算法是否有存在的
* Fragment也有自己的生命周期，会受到Activity的生命周期影响