# Maven Configuration on vscode
Visual Studio Code is great tool for developers, but sometimes it lacks out-of-the-box features present on other IDEs.

Maven is another fantastic tool for Java developers, but one issue I was having is that when using external libraries I wasn't able to visualize javadocs and properly decompiled classes directly on the source code.

## Single project approach
In the project's root for the sources and javadoc respectively:
```cmd
mvn dependency:sources
mvn dependency:resolve -Dclassifier=javadoc
```
If you have a project open on VsCode reload maven project. You should be able to see the docs inside every source code (if available) and 

## Global configuration approach
To make maven install javadoc and sources on all java projects put this inside the `settings.xml` on you local maven repository:

```xml
<profiles>
    <profile>
        <id>download-sources</id>
        <properties>
            <downloadSources>true</downloadSources>
            <downloadJavadocs>true</downloadJavadocs>
        </properties>
    </profile>
</profiles>
<activeProfiles>
    <activeProfile>download-sources</activeProfile>
</activeProfiles>
```
