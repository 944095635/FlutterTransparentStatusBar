# FlutterTransparentStatusBar
透明任务栏，沉浸式任务栏





主要核心内容：

````xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <style name="LaunchTheme" parent="@android:style/Theme.Light.NoTitleBar">
        <item name="android:windowBackground">@drawable/launch_background</item>
        <!--任务栏透明-->
        <item name="android:statusBarColor">@android:color/transparent</item>
        <item name="android:windowTranslucentStatus">true</item>
    </style>
    <style name="NormalTheme" parent="@android:style/Theme.Light.NoTitleBar">
        <item name="android:windowBackground">?android:colorBackground</item>
        <!-- <item name="android:navigationBarColor">@android:color/transparent</item> -->
        <!-- <item name="android:windowFullscreen">true</item> -->
        <!--窗口透明 只有小米手机支持-->
        <!-- <item name="android:windowTranslucentStatus">true</item> -->
        <!--任务栏透明-->
        <item name="android:statusBarColor">@android:color/transparent</item>
    </style>
</resources>
````

注释的行 仅仅只有小米手机支持，如果取消注释，其他手机会出现黑色条纹，保持代码注释，所有手机的都支持。但是启动的时候顶部会 闪过一个黑条。目前没有解决

//设置任务栏透明
//setBarStatus(false);

```dart
setBarStatus(bool isDarkIcon, {Color color: Colors.transparent}) async {
  if (Platform.isAndroid) {
    if (isDarkIcon) {
      SystemUiOverlayStyle systemUiOverlayStyle = SystemUiOverlayStyle(
          statusBarColor: color,
          statusBarIconBrightness: Brightness.dark,
          statusBarBrightness: Brightness.light);
      SystemChrome.setSystemUIOverlayStyle(systemUiOverlayStyle);
    } else {
      SystemUiOverlayStyle systemUiOverlayStyle = SystemUiOverlayStyle(
          statusBarColor: color,
          statusBarIconBrightness: Brightness.light,
          statusBarBrightness: Brightness.dark);
      SystemChrome.setSystemUIOverlayStyle(systemUiOverlayStyle);
    }
  }
}
```
