---
layout: page
title: "Helidon & Java SE Preview Features Cheat Sheet"
excerpt: "I often use Helidon to demo new Java SE features, including Preview Features (ex. Record classes, Sealed classes, etc). This simple cheat sheet explains how to use Java SE Preview Features with Helidon…"
---

<br>
I often use [Helidon](https://helidon.io/#/) to demo new Java SE features, including [Preview Features](https://openjdk.java.net/jeps/12) (ex. Record classes, Sealed classes, etc). This simple cheat sheet explains how to use Java SE features with Helidon.

<br>
<p align="center">
	<img alt="book cover" src="/images/blog/paul-skorupskas-7KLa-xLbSXA-unsplash.jpg" style="box-shadow: 0px 0px 20px 0px rgba(0,0,0,0.5);"/>
	<span>Photo by <a href="https://unsplash.com/@pawelskor?utm_source=unsplash&amp;utm_medium=referral&amp;utm_content=creditCopyText">Paul Skorupskas</a></span>
</p>
<br>

As a reminder, Java SE Preview Features should explicitly be enabled at both compile-time and run-time. This is done by simpling passing the `--enable-preview` flag to the javac compiler, or to the JVM. For more details on Java SE Preview Features, check this [article](https://blogs.oracle.com/javamagazine/the-role-of-preview-features-in-java-14-java-15-java-16-and-beyond).

<h3>Compile-time</h3>

To enable Preview Features at compile-time, update the Helidon project's `pom.xml`. Make sure to specify the Java version you are using.

```xml
<plugin>
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-compiler-plugin</artifactId>
   <version>3.8.0</version>
   <configuration>
      <compilerArgs>--enable-preview</compilerArgs>
      <release>16</release>
   </configuration>
</plugin>
```

<h3>Testing</h3>

To enable Preview Features during tests, update the Helidon project's `pom.xml`.

```xml
<plugin>
   <groupId>org.apache.maven.plugins</groupId>
   <artifactId>maven-surefire-plugin</artifactId>
   <version>3.0.0-M5</version>
   <configuration>
      <argLine>--enable-preview</argLine>
   </configuration>
</plugin>
```

<h3>Run-time</h3>

If the Helidon application is **launched from the command line**, simply pass the flag to the JVM.

➭ `java --enable-preview -jar target/bare-se.jar`

<p style="text-align: center;">-</p>

If you are using the **Helidon CLI DevLoop**, pass the argument to the JVM when starting the DevLoop. 

➭ `helidon dev --app-jvm-args "--enable-preview"`

<p style="text-align: center;">-</p>

If you are using the Maven plugin to generate, via `jlink` a **custom Java runtime image** for your Helidon application, you can specify argument(s) that should be passed to the JVM.

➭ `mvn package -Pjlink-image -Djlink.image.defaultJvmOptions="--enable-preview"`

The Helidon application can then be lanched via the generated script.

➭ `target/bare-se-jri/bin/start`

<p style="text-align: center;">-</p>

If the Helidon application is **containerized**, just update its `Dockerfile`.

```
…
CMD ["java", "--enable-preview", "-jar", "bare-se.jar"]
```
<p style="text-align: center;">~</p>


