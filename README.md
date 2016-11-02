# ImageSelector
此demo包含了图片的多选、单选、裁剪、预览，我是很久前在某个论坛上下载的，不过已经忘了是哪个论坛的，所有在这里声明下，总之很感谢开源的那位大牛，这个demo非常值得学习。
调用也很简单，如果单独抽出来执行时改改下面的这个代码就行了<br>
```Java
/**
 * maxSelectNum --> 可选择图片的数量
 * mode         --> 单选 or 多选
 * isShow       --> 是否显示拍照选项
 * isPreview    --> 是否打开预览选项
 * isCrop       --> 是否打开剪切选项
 */
ImageSelectorActivity.start(MainActivity.this, maxSelectNum, mode, isShow,isPreview,isCrop);
```

![](https://raw.githubusercontent.com/ioneday/ImageSelector/master/screenshot/Screenshot1.jpg)
![](https://raw.githubusercontent.com/ioneday/ImageSelector/master/screenshot/Screenshot2.jpg)
![](https://raw.githubusercontent.com/ioneday/ImageSelector/master/screenshot/Screenshot3.jpg)

![](https://raw.githubusercontent.com/ioneday/ImageSelector/master/screenshot/Screenshot4.jpg)
![](https://raw.githubusercontent.com/ioneday/ImageSelector/master/screenshot/Screenshot5.jpg)

## Quick start

1) Add Library module as a dependency in your build.gradle file.

or

```xml
dependencies {
    compile 'com.android.support:recyclerview-v7:22.2.1'
    compile 'com.github.bumptech.glide:glide:3.6.1'
    compile 'com.commit451:PhotoView:1.2.4'
    compile 'com.isseiaoki:simplecropview:1.0.13'
    compile 'com.yongchun:com.yongchun.imageselector:1.1.0'
}
```

2) Declare permission in your AndroidManifest.xml

```xml
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```
```java
<activity android:name="com.yongchun.library.view.ImageSelectorActivity"/>
<activity android:name="com.yongchun.library.view.ImagePreviewActivity"/>
<activity android:name="com.yongchun.library.view.ImageCropActivity"/>
```

3) Call ImageSelectorActivity in your code

```java
ImageSelectorActivity.start(MainActivity.this, maxSelectNum, mode, isShow,isPreview,isCrop);
```
same this

```java
public static void start(Activity activity, int maxSelectNum, int mode, boolean isShow, boolean enablePreview, boolean enableCrop) {
    Intent intent = new Intent(activity, ImageSelectorActivity.class);
    intent.putExtra(EXTRA_MAX_SELECT_NUM, maxSelectNum);
    intent.putExtra(EXTRA_SELECT_MODE, mode);
    intent.putExtra(EXTRA_SHOW_CAMERA, isShow);
    intent.putExtra(EXTRA_ENABLE_PREVIEW, enablePreview);
    intent.putExtra(EXTRA_ENABLE_CROP, enableCrop);
    activity.startActivityForResult(intent, REQUEST_IMAGE);
}
```
4) Receive result in your onActivityResult Method

``` java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    if(resultCode == RESULT_OK && requestCode == ImageSelectorActivity.REQUEST_IMAGE){
        ArrayList<String> images = (ArrayList<String>) data.getSerializableExtra(ImageSelectorActivity.REQUEST_OUTPUT);
        // do something
    }
}
```

## Thanks

* [Glide](https://github.com/bumptech/glide)

* [PhotoView](https://github.com/chrisbanes/PhotoView)

* [simplecropview](https://github.com/IsseiAoki/SimpleCropView)

###License
>The MIT License (MIT)

>Copyright (c) 2015 Dee

>Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

>The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
