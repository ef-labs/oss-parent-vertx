# Englishtown oss-parent-vertx
This should be the parent pom for Englishtown OSS vert.x maven projects.


## Configuration
Add the following to your pom:

### Parent pom

```xml
    <parent>
        <groupId>com.englishtown</groupId>
        <artifactId>oss-parent-vertx</artifactId>
        <version>1.0.0</version>
    </parent>
```

### Distribution site element.

This cannot be added in the parent due to this issue: http://jira.codehaus.org/browse/SCM-531

```xml
    <distributionManagement>
        <site>
            <id>sling.englishtown.com</id>
            <url>
                dav:https://sling.englishtown.com/content/docs/${project.groupId}/${project.artifactId}/${project.version}
            </url>
        </site>
    </distributionManagement>
```

### SCM element

This cannot be added in the parent due to this issue: http://jira.codehaus.org/browse/SCM-531


```xml
    <scm>
        <connection>scm:git:https://github.com/englishtown/${project.artifactId}.git</connection>
        <developerConnection>scm:git:ssh://git@github.com/englishtown/${project.artifactId}.git</developerConnection>
        <tag>HEAD</tag>
        <url>https://github.com/englishtown/${project.artifactId}</url>
    </scm>
```

### Maven plugins

```xml
    <build>
        <plugins>
            <plugin>
                <groupId>io.vertx</groupId>
                <artifactId>vertx-maven-plugin</artifactId>
                <!--
                You can specify a configFile and number of instances to run for the runMod task here if you want
                <configuration>
                    <configFile>/path/to/MyVerticle.conf</configFile>
                    <instances>1</instances>
                </configuration>
                -->
            </plugin>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-assembly-plugin</artifactId>
            </plugin>
        </plugins>
    </build>
```


## Example commands

### Snapshot deployment
mvn clean deploy

### jgitflow
mvn jgitflow:release-start

mvn jgitflow:release-finish
