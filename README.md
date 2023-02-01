# compose_intellij_dependencies
compose_intellij_dependencies

Using this shared dependency, you can use compose to write a plugin UI for idea without worrying about your plugin size up to 60~70 MB, 
The plugin provides a shared base for developing IntelliJ plugins with the
<a href="https://www.jetbrains.com/lp/compose/">Compose</a> UI framework.

It provides Compose classes and native libraries for use at runtime,
so that multiple IntelliJ plugins can share Compose classes and Skia bindings,
You can greatly reduce the size of your plugin, with a minimum of about 100 KB, only including your plugin code jar file

When users download plugins written in Compose, if the plug-in is not installed, IADA will prompt the user to install the plug-in,
and it can be used normally after installation, so that if the user uses multiple plug-ins written in Compose, only need to download a shared dependency,
instead of downloading each plug-in separately, which will reduce the user's disk space.

## How to use this dependency：
1. Edit build.gradle.kts
```kotlin
plugins {
    //...
    id("org.jetbrains.kotlin.jvm") version "1.8.0"
    id("org.jetbrains.intellij") version "1.12.0"
    id("org.jetbrains.compose") version "1.3.0"
    //...
}
```

2. Edit src/main/resources/META-INF/plugin.xml
```xml
   <idea-plugin>
    ...
    <depends>com.wilinz.compose.intellij.dependencies</depends>
    ...
   </idea-plugin>
   ```

3. Edit gradle.properties
```properties
#...
kotlin.stdlib.default.dependency=false
```