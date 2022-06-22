![ic_logo_compass_qibla](https://user-images.githubusercontent.com/32610660/174967545-952b7ceb-1ead-4a1c-81af-bd18de4b2482.png)

# compass-qibla
Android Library to determine Qibla direction

[![](https://jitpack.io/v/derysudrajat/compass-qibla.svg)](https://jitpack.io/#derysudrajat/compass-qibla)


## Setup

Add this to `build.gradle` (project)

```gradle
allprojects {
  repositories {
      ...
      maven { url 'https://jitpack.io' }
    }
}
```

Add this dependency to `build.grdle` (module) or if you using gradle 7+ put it to `setting.gradle`
```gradle
dependencies {
  implementation 'com.github.derysudrajat:compass-qibla:1.0.0'
}
```

## How to use
You can use this library just by add this code 🥳
```kotlin
CompassQibla.Builder(this)
    .onDirectionChangeListener { qiblaDirection -> 
        qiblaDirection.isFacingQibla // boolean variable indentify if you facing qibla
        qiblaDirection.compassAngle // float variable to rotate compass
        qiblaDirection.needleAngle // float variable to rotate compass needle

        // your awesome code here ...
    }.build()
```
The QiblaDirection is data class variable, this is detail about it
<table style="width:100%">
  <tr>
    <th colspan="3">QiblaDirection</th>
  </tr>
  <tr>
    <th>Variable</th>
    <th>Type</th>
    <th>Description</th>
  </tr>
    <tr>
    <td>compassAngle</th>
    <td>Float</th>
    <td>a variable that can use to rotate your compass angle</th>
  </tr>
    </tr>
    <tr>
    <td>needleAngle</th>
    <td>Float</th>
    <td>a variable that can use to rotate your compass needle angle</th>
  </tr>
  <tr>
    <td>isFacingQibla</th>
    <td>Boolean</th>
    <td>a variable that identifies whether you are facing the Qibla or not</th>
  </tr>
</table>

Also, you can configure the permission listener 😎
```kotlin
CompassQibla.Builder(this)
    .onPermissionGranted { permission ->
        // handle if location permission was granted
    }
    .onPermissionDenied { 
        // handle if location permission was denied
    }
    .onDirectionChangeListener { qiblaDirection -> 
        // your awesome code here ...
    }.build()
```

And last but not least if you wondering can I get the location address also? yes, you can! 👀

the Address variable is refer to [`android.location.Address`](https://developer.android.com/reference/android/location/Address) by android
```kotlin
CompassQibla.Builder(this)
    .onGetLocationAddress { address ->
        // handle location address result
    }
    .onDirectionChangeListener { qiblaDirection -> 
        // your awesome code here ...
    }.build()
```

And this is the whole code that you can consume 🔥
```kotlin
CompassQibla.Builder(this)
    .onPermissionGranted { permission ->
        // handle if location permission was granted
    }
    .onPermissionDenied {
        // handle if location permission was denied
    }
    .onGetLocationAddress { address ->
        // handle location address result
    }
    .onDirectionChangeListener { qiblaDirection ->
        // your awesome code here ...
    }.build()
```

Keep chill and enjoyy 😎✨
