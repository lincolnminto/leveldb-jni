# LevelDB Android JNI

Is very fast easy to use key-value database for Android 

[![Build Status](https://travis-ci.org/jacek-marchwicki/leveldb-jni.svg?branch=master)](https://travis-ci.org/jacek-marchwicki/leveldb-jni)

## How to build

```bash
git submodule update --init && ./gradlew build
```

## How to use

Add to your `build.gradle` file:

```gradle
repositories {
    maven {
        url 'https://dl.bintray.com/jacek-marchwicki/maven/'
    }
}
dependencies {
    compile 'com.appunite:lib-leveldb-jni:0.0.7'
}
```

type in your code:

```java
byte[] KEY = "key".getBytes();
final LevelDB db = new LevelDB(context.getDatabasePath("database.leveldb").getAbsolutePath());
db.putString(KEY, "value".getBytes());
final String value = new String(db.getString(KEY));
db.close();
```

More examples available in [test class](lib-leveldb-jni/src/androidTest/java/com/appunite/leveldb/LevelDBTest.java)

## Proguard

This is very short library so you can simple add everything to proguard keep:

```proguard
-keepclassmembers class com.appunite.leveldb.* {
    *;
}
```

## Credits

- Thanks to Nabil HACHICHA for writing SnappyDB https://github.com/nhachicha/SnappyDB
- Thanks to Moyang Wang for writing https://github.com/googolmo/Leveldb-Android
- Thanks to Google folks for writing https://github.com/google/leveldb and https://github.com/google/snappy
- Thanks to for Android tools team for writing ndk plugin http://tools.android.com/tech-docs/new-build-system/gradle-experimental

## License

```
Copyright [2016] <jacek.marchwicki@gmail.com>

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

### Upload to bintary

```bash
./gradlew build install
./gradlew :lib-leveldb-jni:bintrayUpload
```

### Add this Dependency from github

Step 1. Add the JitPack repository to build.gradle at the end of repositories:

```gradle
repositories {
    // ...
    maven { url "https://jitpack.io" }
}
```
Step 2. Add the dependency in the form

```gradle
dependencies {
    compile 'com.github.lincolnminto:leveldb-jni:0.0.8'
}
```

It is possible to build the latest commit on the master branch, for example :

```gradle
dependencies {
    compile 'com.github.lincolnminto:leveldb-jni:master-SNAPSHOT'
}
```
