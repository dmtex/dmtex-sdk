# DMTex SDK packages

Provides build tools such as parent POM, CheckStyle and PMD settings.

## Parent POM _dmtex-parent_

POM provides several Maven profiles that can be used in descending projects.

### groovy

Activated when directory */src/main/groovy* exists.

Provides tools for Groovy classes processing.

### kotlin

Activated when directory */src/main/kotlin* exists.

Provides tools for Kotlin classes processing.

### javadoc

Activated explicitly by **-Pjavadoc**

Generates Javadocs and prepares for deployment.

### source

Activated explicitly by **-Psource**

Generates sources (including test sources) and prepares for deployment.

### pdf

Activated explicitly by **-Ppdf**

Generates PDF documentation from Asciidoc files.
If some configuration attributes need to be changes it can be done inside `attributes` tag like in sample below. 

```xml
  <profiles>
    <profile>
      <id>pdf</id>
      <activation>
        <activeByDefault>true</activeByDefault>
      </activation>
      <build>
        <defaultGoal>process-resources</defaultGoal>
        <plugins>
          <plugin>
            <groupId>org.asciidoctor</groupId>
            <artifactId>asciidoctor-maven-plugin</artifactId>
            <executions>
              <execution>
                <id>generate-pdf-doc</id>
                <configuration>
                  <backend>pdf</backend>
                  <attributes>
                    <source-highlighter>coderay</source-highlighter>
                    <icons>font</icons>
                    <pagenums/>
                    <toc/>
                    <idprefix/>
                    <idseparator>-</idseparator>
                  </attributes>
                </configuration>
              </execution>
            </executions>
          </plugin>
        </plugins>
      </build>
    </profile>
  </profiles>
```

The details of supported attributes can be read at [Document Attributes Reference](https://docs.asciidoctor.org/asciidoc/latest/attributes/document-attributes-ref/)

### html

Activated explicitly by **-Phtml**

Generates HTML documentation from Asciidoc files.
Configuration is similar to `pdf` profile.

### checkstyle

Activated when directory */src/main/java* exists.

Initiates Checkstyle checks on Java sources.

### pmd

Activated by default. To deactivate add property **-DskipPMD**

Initiates PMD checks on code.

### spotbugs

Activated by default. To deactivate add property **-DskipSpotbugs**

Initiates SpotBugs checks on code.

### jacoco

Activated by default. To deactivate add property **-DskipJaCoCo**

Initiates JaCoCo and code coverage.

### pitest

Activated explicitly by **-Dpitest**

Initiates mutation testing.
