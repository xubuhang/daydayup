SystemBarTint设置状态栏（4.4.+）

昨天碰到个问题：我使用开源项目SystemBarTint来设置状态栏颜色却没有变化,他的项目在我手机上却有效果？
  jgilfelt/SystemBarTint · GitHub(https://github.com/jgilfelt/SystemBarTint)
直到今天才解决：
  必须要在
      mTintManager = new SystemBarTintManager(this);
      mTintManager.setStatusBarTintEnabled(true);
      mTintManager.setNavigationBarTintEnabled(true);
  上面加上
      if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.KITKAT) {
    			setTranslucentStatus(true);
	      	}
不知道是不是魅族3的问题还是什么。

又出现新问题：状态栏和自定义标题栏相互阻挡。
    解决：http://blog.csdn.net/carlos1992/article/details/46773059
        1、android:fitsSystemWindows="true"
           android:clipToPadding="true"
        2、布局设置颜色 android:background="#009959"
