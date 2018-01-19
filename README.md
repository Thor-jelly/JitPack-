# JitPack-
提交问题

提交代码失败：
- 更改gradle中apply plugin: 'com.android.application'为apply plugin: 'com.android.library'
- 删除applicationId "com.dongdongwu.maxnumet"，依赖成功
- jitpack代码没有注释

```
//以下为配置library注释在打包jar后保留
    // 打包源码jar
    task sourcesJar(type: Jar) {
        from android.sourceSets.main.java.srcDirs
        classifier = 'sources'
    }
    task javadoc(type: Javadoc) {
        failOnError false
        source = android.sourceSets.main.java.sourceFiles
        classpath += project.files(android.getBootClasspath().join(File.pathSeparator))
        classpath += configurations.compile
    }
    // 打包文档jar
    task javadocJar(type: Jar, dependsOn: javadoc) {
        classifier = 'javadoc'
        from javadoc.destinationDir
    }
    artifacts {
        archives sourcesJar
        archives javadocJar
    }
```
