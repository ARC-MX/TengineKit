[中文版本](docs/README_CN.md)

![TengineKit](https://openailab.oss-cn-shenzhen.aliyuncs.com/logo/TengineKit.png?raw=true "TengineKit logo")
=======================================================================

# TengineKit - Free RealTime Face Landmarks 212 Points For Mobile.  
[![Apache 2.0](https://img.shields.io/crates/l/r)](LICENSE)     

TengineKit, developed by OPEN AI LAB.       
TengineKit is an easy-to-integrate face detection and face landmarks SDK. At present, it can run on various mobile phones at very low latency.**We will continue to update this project for better results and better performance!**

# Effect

| Face Detection &</br> Face 2dLandmark | Face 3dLandmark &</br>Iris | Upper Body Detection &</br> Uppper Body Landmark | Hand Detection &</br> Hand Landmark |
| :---: | :---: | :---: | :---: |
| <div align=center><img width="150" height="270"  src="https://openailab.oss-cn-shenzhen.aliyuncs.com/images/TengineKitDemo4.gif"/></div> | <div align=center><img width="150" height="270"  src="https://openailab.oss-cn-shenzhen.aliyuncs.com/images/face2.gif"/></div> | <div align=center><img width="150" height="270"  src="https://openailab.oss-cn-shenzhen.aliyuncs.com/images/body3.gif"/></div> | <div align=center><img width="150" height="270"  src="https://openailab.oss-cn-shenzhen.aliyuncs.com/images/hand2.gif"/></div> |



## Gif
<div align=center><img width="800" height="400"  src="https://openailab.oss-cn-shenzhen.aliyuncs.com/images/object_face_landmark.gif"/></div>
<div align=center><b>dance of host</b></div>

## Video( <a href="https://www.youtube.com/watch?v=bnyD3laX_bU" target="_blank">YouTube</a> | <a href="https://www.bilibili.com/video/BV1AK4y147xx/" target="_blank">BiliBili</a> )
[<div align=center><img width="568" height="320" src="https://openailab.oss-cn-shenzhen.aliyuncs.com/images/landmark_report.png"/></div>](https://youtu.be/bnyD3laX_bU)
<div align=center><img src="https://img.shields.io/youtube/views/bnyD3laX_bU?style=social"/></div>

# Have a try
- [Apk](apk/TengineKitDemo-v1.2.2.apk) can be directly downloaded and installed on the phone to see the effect.

or

- scan code to download apk 

![Apk](https://www.pgyer.com/app/qrcode/A0uD?sign=&auSign=&code=)

# Goals
- Provide best performance in mobile client
- Provide the simplest API in mobile client
- Provide the smallest package  in mobile client

# Features
- face detection
- face landmarks
- face 3dlandmarks
- face attributes like age, gender, smile, glasses
- eye iris & landmarks
- hand detect(Real-time, not yet on Mobile)
- hand landmarks(Real-time, not yet on Mobile)
- body detect(Real-time, not yet on Mobile)
- body landamrks(Real-time, not yet on Mobile)

# Performance(face & landmark)

| CPU | Time consuming | Frame rate |
| :---: | :---: | :---: |
| Kirin 980 | 14ms | 71fps | 
| Qualcomm 855 | 15ms | 67fps |
| Kirin 970 | 17ms | 59fps |
| Qualcomm 835 | 18ms | 56fps |
| Kirin 710F| 19ms | 53fps |
| Qualcomm 439 | 26ms | 38fps |
| MediaTek Helio P60 | 27ms | 37fps |
| Qualcomm 450B | 28ms | 36fps |

# Gradle Configure
The ```build.gradle``` in Project add
```java
    repositories {
        ...
        jcenter()
        mavenCentral()
        ...
    }

    allprojects {
        repositories {
            ...
            jcenter()
            mavenCentral()
            ...    
        }
    }
    
```     
The ```build.gradle``` in Main Module add,select which function you need.But the ```core``` is must.
```java
    dependencies {
        ...
        // Must!!!!
        implementation 'com.tengine.tenginekit:core:0.0.1'
        // Function on Face
        implementation 'com.tengine.tenginekit:face:0.0.1'
        // Function on Hand
        implementation 'com.tengine.tenginekit:hand:0.0.1'
        // Function on Body
        implementation 'com.tengine.tenginekit:body:0.0.1'
        ...
    }
```     

# System
Android
- Min Sdk Version 19

# API
When using sdk, you can refer to [Api](docs/Api.md) to complete the functions you need.

# Landmark Points Order
[Landmark Points Order](docs/POINTORDER.md)

# Usage
[Usage](docs/Usage.md)

# Permission
``` permission
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.INTERNET"/>

<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
<uses-permission android:name="android.permission.READ_PHONE_STATE"/>

<uses-permission android:name="android.permission.CAMERA"/>
```


# Sample
Android code under the "sample/" folder.
# Access Guide
In setRotation of TengineKit Api, there are two parameters ori and is_screen_rotate, which are the rotation angle and whether to follow the screen rotation. Whether the android:screenOrientation parameter in the Manifest follows the screen can be set. Not setting this parameter is to follow the screen rotation.
# Process
## 1.Device preview
This part is to get data from Camera, as the SDK input.
## 2.Angle
We use the vertical screen as an angle of 0 degrees. Since the data collected by the Android camera always deviates by 90, it is necessary to set + (-90) when setting the ori parameter. The actual rotation angle of Android is to add a function through the sensor Calculate to get. For details, see the example in the Demo project.
## 3.Rendering
When rendering, it is rendered at an angle of 0°, which is the normal output that people see under normal circumstances. The Android part has Canvas and Opengl rendering. Using Opengl rendering can make your apk better.

# Contact
About the use of TengineKit and face-related technical exchanges, you can join the following QQ groups(Group Answer:TengineKit):
- TengineKit communication QQ group: 630836519
- Scan to join group
 
 <img width="256" height="256"  src="https://openailab.oss-cn-shenzhen.aliyuncs.com/images/QQGroup_QR.jpg"/>


# ImageHandle
[ImageHandle](docs/Api.md#ImageHandleApi) to do Zoom, rotate, crop, and change picture format