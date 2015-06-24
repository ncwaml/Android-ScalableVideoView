# ScalableVideoView

Android Texture VideoView having a variety of scale types like the scale types of ImageView.  

# Release Note

[Release Note] (https://github.com/yqritc/Android-ScalableVideoView/releases)

# Gradle (coming soon)
```
repositories {
    jcenter()
}

dependencies {
    compile 'com.yqritc:android-scalablevideoview:1.0.0'
}
```

# Support Scale Types  

### Scale to fit 
- fitXY
- fitStart
- fitCenter
- fitEnd

### No Scale
- leftTop
- leftCenter
- leftBottom
- centerTop
- center
- centerBottom
- rightTop
- rightCenter
- rightBottom

### Crop
- leftTopCrop
- leftCenterCrop
- leftBottomCrop
- centerTopCrop
- centerCrop
- centerBottomCrop
- rightTopCrop
- rightCenterCrop
- rightBottomCrop

### Scale Inside
- startInside
- centerInside
- endInside


# Usage

### Set scale type in layout file
```
<com.yqritc.scalablevideoview.ScalableVideoView
  android:id="@+id/video_view"
  android:layout_width="match_parent"
  android:layout_height="match_parent"
  android:layout_marginBottom="100dp"
  app:scalableType="fitCenter"/>
```
Please refere the following xml for the list of scalableType you can set.  
[attrs.xml](https://github.com/yqritc/Android-ScalableVideoView/blob/master/library/src/main/res/values/attrs.xml)

### Sample usage in source code
```
@Override
protected void onCreate(Bundle savedInstanceState) {
  super.onCreate(savedInstanceState);
  setContentView(R.layout.activity_main);
  
  mVideoView = (ScalableVideoView) findViewById(R.id.video_view);
  try {
    mVideoView.setRawData(R.raw.landscape_sample);
  } catch (IOException ioe) {
    //handle error
  }
}

@Override
public void onClick(View v) {
  switch (v.getId()) {
    case R.id.btn_start:
        mVideoView.start();
        break;
    case R.id.btn_update_scale:
        mVideoView.setScalableType(ScalableType.CENTER_TOP_CROP);
        mVideoView.invalidate();
        break;
      default:
        break;
  }
}
```
[ScalableVideoView](https://github.com/yqritc/Android-ScalableVideoView/blob/master/library/src/main/java/com/yqritc/scalablevideoview/ScalableVideoView.java) is extending TextureView to play video by using MediaPlayer.  
Basic functionalities are defined in this class to play and scale video.  
If you need to control more, extend this class and define your custom video view.  


# License
```
Copyright 2015 yqritc

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
