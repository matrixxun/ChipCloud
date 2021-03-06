# ChipCloud
[![Release](https://jitpack.io/v/fiskurgit/ChipCloud.svg)](https://jitpack.io/#fiskurgit/ChipCloud) [![Build Status](https://travis-ci.org/fiskurgit/ChipCloud.svg?branch=master)](https://travis-ci.org/fiskurgit/ChipCloud) [![license](https://img.shields.io/github/license/mashape/apistatus.svg?maxAge=2592000)](https://github.com/fiskurgit/ChipCloud/blob/master/LICENSE) [![Codacy Badge](https://api.codacy.com/project/badge/Grade/55d686ee370d494b9f7f7e6636c0c294)](https://www.codacy.com/app/fiskur/ChipCloud?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=fiskurgit/ChipCloud&amp;utm_campaign=Badge_Grade) [![Gitter](https://img.shields.io/gitter/room/nwjs/nw.js.svg?maxAge=2592000)](https://gitter.im/fiskurgit/fiskur) 
<a href="http://www.methodscount.com/?lib=com.github.fiskurgit%3AChipCloud%3A2.1.0"><img src="https://img.shields.io/badge/Size-27 KB-e91e63.svg"/></a>

ChipCloud is an Android view (very) quickly knocked up for a larger hackathon project, it creates a wrapping cloud of '[Chips](https://www.google.com/design/spec/components/chips.html)'. Basic demo [available on the Play Store](https://play.google.com/store/apps/details?id=eu.fiskur.chipclouddemo) 

![Trainer Sizes](images/trainer_sizes.png)

## Usage

Add to your Android layout xml:
```xml
<eu.fiskur.chipcloud.ChipCloud
    android:id="@+id/chip_cloud"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"/>
```

Configure in xml:  
```xml
<eu.fiskur.chipcloud.ChipCloud
    xmlns:chipcloud="http://schemas.android.com/apk/res-auto"
    android:id="@+id/chip_cloud"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    chipcloud:deselectedColor="@color/deselected_color"
    chipcloud:deselectedFontColor="@color/deselected_font_color"
    chipcloud:selectedColor="@color/selected_color"
    chipcloud:selectedFontColor="@color/selected_font_color"
    chipcloud:deselectTransitionMS="500"
    chipcloud:selectTransitionMS="750"
    chipcloud:labels="@array/labels"
    chipcloud:selectMode="required"/>
```
or in code:  
```java
ChipCloud chipCloud = (ChipCloud) findViewById(R.id.chip_cloud);

new ChipCloud.Configure()
        .chipCloud(chipCloud)
        .selectedColor(Color.parseColor("#ff00cc"))
        .selectedFontColor(Color.parseColor("#ffffff"))
        .deselectedColor(Color.parseColor("#e1e1e1"))
        .deselectedFontColor(Color.parseColor("#333333"))
        .selectTransitionMS(500)
        .deselectTransitionMS(250)
        .labels(someStringArray)
        .mode(ChipCloud.Mode.MULTI)
        .chipListener(new ChipListener() {
            @Override
            public void chipSelected(int index) {
                //...
            }
            @Override
            public void chipDeselected(int index) {
                //...
            }
        })
        .build();
```

Add items dynamically too:
```java
chipCloud.addChip("Foo");
chipCloud.addChip("Bar");

//or

chipCloud.addChips(someStringArray);
```

Set the selected index using ```chipCloud.setSelectedChip(2)```

Real-world example for shoe sizes:  
![Shoe Sizes](images/wrapping_example.png)

## Modes

```java
public enum Mode {
  SINGLE, MULTI, REQUIRED, NONE
}
```

The default mode is single choice (where it's valid to have no chip selected), if you want a RadioGroup manadatory style where once a chip is selected there must always be a selected item use ```chipCloud.setMode(ChipCloud.Mode.REQUIRED);``` (or set in xml or the builder). There's a multiple select mode too: ```chipCloud.setMode(ChipCloud.Mode.MULTIPLE);```. If you want to deactiviate selecting of chips you can set the select mode to ```chipCloud.setMode(ChipCloud.Mode.NONE);```.

## Dependency

Add jitpack.io to your root build.gradle, eg:

```groovy
allprojects {
    repositories {
        jcenter()
        maven { url "https://jitpack.io" }
    }
}
```

then add the dependency to your project build.gradle:

```groovy
dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.github.fiskurgit:ChipCloud:2.1.0'
}
```
You can find the latest version in the releases tab above: https://github.com/fiskurgit/ChipCloud/releases

More options at jitpack.io: https://jitpack.io/#fiskurgit/ChipCloud

##Licence

Full licence here: https://github.com/fiskurgit/ChipCloud/blob/master/LICENSE

In short:

> The MIT License is a permissive license that is short and to the point. It lets people do anything they want with your code as long as they provide attribution back to you and don’t hold you liable.
