###issue
Maven跑的时候报错：

```
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.1:testCompile (default-testCompile) on project webtest: Compilation failure

[ERROR] No compiler is provided in this environment. Perhaps you are running on a JRE rather than a JDK?
```
###solution
在pom.xml文件里面显式指定jdk

```
<build>
    <plugins>
        <plugin>
            <groupId>org.springframework.boot</groupId>
            <artifactId>spring-boot-maven-plugin</artifactId>
        </plugin>
        <plugin>
            <artifactId>maven-compiler-plugin</artifactId>
            <version>3.1</version>
            <configuration>
                <fork>true</fork>
                <executable>D:\jdk1.7.0_25\bin\javac.exe</executable>
            </configuration>
        </plugin>
    </plugins>
</build>
```
[http://www.kriblog.com/ide/sts/error-no-compiler-is-provided-in-this-environment.-perhaps-you-are-running-on-a-jre-rather-than-a-jdk.html](http://www.kriblog.com/ide/sts/error-no-compiler-is-provided-in-this-environment.-perhaps-you-are-running-on-a-jre-rather-than-a-jdk.html)

