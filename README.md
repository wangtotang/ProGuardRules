# ProGuardRules

　　这个工程项目收集了大量框架的ProGuard规则配置,在开发过程中，如果需要添加各个框架ProGuard的配置规则，可以参考
工程下的Android·Library·Module的`proguardrules/rules`目录，一个文件就是一个框架的ProGuard规则。

### Usage

　　这里提供三种使用方法，依个人爱好决定。

##### 1.Gradle Dependencies

* ProGuardRules:[ ![Download](https://api.bintray.com/packages/wangtotang/maven/proguardrules/images/download.svg) ](https://bintray.com/wangtotang/maven/proguardrules/_latestVersion)

```groovy
   dependencies {
       compile 'com.tong.proguardrules:proguardrules:latest.release'
   }
```
##### 2.FileTree

  在`src`同级目录下新建文件夹，如`rules`，然后将需要的配置规则文件复制进去，然后进行以下配置。

```groovy
   android {
       ...
       buildTypes {
           release {
               ...
               minifyEnabled true
               proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
               proguardFiles fileTree(dir: 'rules', include: ['*.pro']).asList().toArray()
           }
       }
   }
```

  * 在Gradle Plugin 2.2.0 以下，还可以使用以下语法：

```groovy
   android {
       ...
       buildTypes {
           release {
               ...
               minifyEnabled true
               proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
               FileCollection proguardFileCollection = files { file('./rules').listFiles() }
               proguardFiles(proguardFileCollection)
           }
       }
   }
```

##### 3.Files

  直接将文件复制到`proguard-rules.pro`同级目录下，然后进行以下配置。

```groovy
   android {
       ...
       buildTypes {
           release {
               ...
               minifyEnabled true
               proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
               proguardFile 'proguard-eventbus.txt'
               proguardFile 'proguard-google-play-services.txt'
               proguardFile 'proguard-gson.txt'
           }
       }
   }
```
### Libraries

　　这些ProGuard规则包含以下的框架：

* [ACRA 4.5.0](https://github.com/ACRA/acra)
* [ActionBarSherlock 4.4.0](http://actionbarsherlock.com/)
* [ActiveAndroid](http://www.activeandroid.com/)
* [Adjust](https://github.com/adjust/android_sdk)
* [Amazon Web Services 1.6.x / 1.7.x](https://aws.amazon.com/releasenotes/Android/1855915734308772)
* [Amazon Web Services 2.1.x](https://github.com/aws/aws-sdk-android)
* [AndroidAnnotations](http://androidannotations.org/)
* [android-gif-drawable](https://github.com/koral--/android-gif-drawable)
* [Apache Avro](http://http://avro.apache.org/)
* [Alibaba Fastjson](https://github.com/alibaba/fastjson)
* [Butterknife](http://jakewharton.github.io/butterknife/)
* [Baidu](http://lbsyun.baidu.com/index.php?title=android-locsdk)
* [Crashlytics 1.+ / 2.+](http://try.crashlytics.com/sdk-android/)
* [Crittercism](http://docs.crittercism.com/android/android.html)
* [EventBus 2.0.2](https://github.com/greenrobot/EventBus)
* [Facebook 3.2.0](https://developers.facebook.com/docs/android/)
* [Facebook Conceal](https://facebook.github.io/conceal/)
* [Facebook Stetho](https://facebook.github.io/stetho/)
* [Facebook Fresco](https://github.com/facebook/fresco)
* [Flurry 3.4.0](http://support.flurry.com/index.php?title=Analytics/Code/ReleaseNotes/Android)
* [Google Analytics 3.0+](https://developers.google.com/analytics/devguides/collection/android/v3/)
* [Google Guava](https://code.google.com/p/guava-libraries/)
* [Google Play Services 4.3.23](http://developer.android.com/google/play-services/setup.html)
* [GreenDao](http://greendao-orm.com/)
* [Glide](https://github.com/bumptech/glide)
* [GSON](https://code.google.com/p/google-gson/)
* [Jackson 2.x](http://wiki.fasterxml.com/JacksonHome)
* [Joda-Convert 1.6](http://www.joda.org/joda-convert/)
* [Joda-Time 2.3](http://www.joda.org/joda-time/)
* [Jsoup](http://jsoup.org/)
* [LoganSquare](https://github.com/bluelinelabs/LoganSquare)
* [New Relic](https://docs.newrelic.com/docs/mobile-monitoring/mobile-sdk-api/new-relic-mobile-sdk-api/working-android-sdk-api)
* [Parse](https://parse.com/products/android)
* [Realm](http://realm.io/news/realm-for-android/)
* [RxJava](https://github.com/ReactiveX/RxJava/wiki/The-RxJava-Android-Module)
* [RxJava-Promises](https://github.com/darylteo/rxjava-promises)
* [Retrolambda](https://github.com/orfjackal/retrolambda)
* [Support Library](https://developer.android.com/tools/support-library/features.html)
* [Sqlite](http://www.sqlite.org/index.html)
* [Square Dagger](https://github.com/square/dagger)
* [Square OkHttp](http://square.github.io/okhttp/)
* [Square Okio](https://github.com/square/okio)
* [Square Otto](http://square.github.io/otto/)
* [Square Picasso](https://github.com/square/picasso)
* [Square Retrofit](http://square.github.io/retrofit/)
* [Square Wire](https://github.com/square/wire)
* [SVG Android](https://github.com/pents90/svg-android)
* [Icepick](https://github.com/frankiesardo/icepick)
* [Simple-Xml](http://simple.sourceforge.net/)
* [Tencent Bugly](http://bugly.qq.com/)

### Thanks

　　这个工程主要参考了[android-proguard-snippets](https://github.com/krschultz/android-proguard-snippets)。并在
此基础上更新了部分文件内容，在此感谢原作者。

### Bugs and Feedback

　　如果有bugs,文件更新要求以及讨论，可以提[issues].

### LICENSE

    Copyright 2017 the ProGuardRules Author

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.

[issues]:https://github.com/wangtotang/ProGuardRules/issues
