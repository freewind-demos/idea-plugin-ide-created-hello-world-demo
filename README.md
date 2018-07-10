Idea Plugin Hello World Demo
===============================================

Notice: Please use [idea-plugin-hello-world-demo](https://github.com/idea-demos/idea-plugin-hello-world-demo) as base project, which is controlled buy gradle, much better than this one.

Add a new action(menu) `hello`, clicking on it will result in showing a dialog.

Please make sure you have unique plugin id and name in `resources/META-INF/plugin.xml`:

```xml
<id>idea-plugin-ide-created-hello-world-demo</id>
<name>idea-plugin-ide-created-hello-world-demo</name>
```

If clicking on the menu shows nothing
-------------------------------------

The main problem is the JDK using is one of OpenJDK/Oracle, and has some bugs. Instead, we need to use the modified jdk provided by JetBrains itself.

- open <https://bintray.com/jetbrains/intellij-jdk/openjdk8-osx-x64/1293.1#files>
- download the later one, which is jdk
- extract it to disk, e.g. `/Users/freewind/dev`
- create file `/Users/freewind/Library/Preferences/IdeaIC2018.1/idea.jdk`, with content `/Users/freewind/dev/jbsdk8u152b1293.1_osx_x64/jdk`
- start idea
- add `jdk`: choose the new downloaded one, give it a name, like `jetbrains-jdk-1.8-fix`
- add new `IntelliJ Platform Plugin SDK`: use `jetbrains-jdk-1.8-fix` as internal jdk

Then start the plugin again.

The article has some information about the jdk changing, but the methods it provided is not working, since the jdk downloaded by the "JB SDK Bintray Downloader" is too old for current IDEAs: <https://intellij-support.jetbrains.com/hc/en-us/articles/206544879-Selecting-the-JDK-version-the-IDE-will-run-under>

If new code doesn't seem working
--------------------------------

Uninstall the plugin from the new created idea instance, then rerun the plugin. (maybe take several times) 
