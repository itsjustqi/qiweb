---
title: Auto-weka issue
author: Qi Li
slug: auto-weka-issue
date: 2018-10-29
categories: []
tags: []
---
When I running auto-weka to build models, an error was displayed as follows:
```
ClassNotFoundException: [weka.core.WekaPackageLibIsolatingClassLoader (Auto-WEKA)] Unable to find class: javax.xml.bind.JAXBContext
```
According to this [solution](https://stackoverflow.com/questions/43574426/how-to-resolve-java-lang-noclassdeffounderror-javax-xml-bind-jaxbexception-in-j%EF%BC%89), this problem is probably casused by Java version as the relevant Java EE API modules have been removed in Java 11.

This issue can be fixed out through the instruction in the above article. While, I choose a different way as follows:

1.Check Java version:
```
/usr/libexec/java_home -V
```

It shows:
```
Qis-Mac:libexec qili$ /usr/libexec/java_home -V
Matching Java Virtual Machines (2):
    11.0.1, x86_64:	"Java SE 11.0.1"	/Library/Java/JavaVirtualMachines/jdk-11.0.1.jdk/Contents/Home
    1.8.0_191, x86_64:	"Java SE 8"	/Library/Java/JavaVirtualMachines/jdk1.8.0_191.jdk/Contents/Home
    /Library/Java/JavaVirtualMachines/jdk-11.0.1.jdk/Contents/Home
```
2.Change Java from version 11 to 8

```
export JAVA_HOME=`/usr/libexec/java_home -v 1.8`
```