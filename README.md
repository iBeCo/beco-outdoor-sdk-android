# Beco Outdoor SDK Demo 


Steps to use the outdoor SDK


### Adding Dependency

In Project build.gradle add

```
allprojects{
	repositories{
		maven { url "https://raw.githubusercontent.com/iBeCo/beco-outdoor-sdk-android/release" }
	}
}
```

Then in App build.gradle add

```
dependencies{
	implementation 'com.beco.outdoor:sdk:1.1'
}
```

Sync gradle.

### Configuration File 

You should create a beco-services.json file your project directory with the SDK key and enviornment id

```
{
  "project_info": {
    "api_key": "46e0b696979896d8b1ef4118f0ace9b096dc210c",
    "environment_id": "global-village"
  },
  "search_settings": {
    "base_color": ""
  },
  "configuration_version": "1"
}

```

On subsequent changes to the json file, please clean project and rebuild it before running it.

Please check the sample application for more info

### Adding Environment Json Parsing plugin. 

This is required so as to parse the beco-services.json(containing api key and environment id.(json currently available in the demo)

In Project build.gradle add

```
buildscript {
    repositories {
        maven{
            url uri('https://raw.githubusercontent.com/iBeCo/beco-gradle-plugin/master/repo')
        }
    }
	dependencies {
        classpath "org.beco:config:1.0"
    }
}
```
Finally apply plugin in App build.gradle at the bottom of the file

```
apply plugin: 'org.beco.config'
```
### Add Google Map API Key

```
<meta-data
            android:name="com.google.android.geo.API_KEY"
            android:value="YOUR_GOOGLE_API" />
```

### Add Activities to Manifest

```
<activity android:name="com.beco.outdoor.sdk.map.BEMapActivity"
            android:screenOrientation="portrait"
            />
<activity android:name="com.beco.outdoor.sdk.map.search.BESearchActivity"
            android:screenOrientation="portrait"
            />
```

### Implemention

Call the BEMapActivity as you would any other activity from your class.
