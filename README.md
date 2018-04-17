# maven-shaded-log4j-transformer
Transformer implementation to concatenate Log4j2Plugins.dat files due build with Maven Shaded plugin.

How to use:

First download and install the plugin into your local repository with 'mvn install'

You need add a new transformer to your transformers and add the plugin dependency to the shade plugin

An example is below

```
<plugins>
  <plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-shade-plugin</artifactId>
    <version>3.1.0</version>
    <executions>
      <execution>
        <phase>package</phase>
        <goals>
          <goal>shade</goal>
        </goals>
        <configuration>
          <transformers>
            <transformer
              implementation="com.github.edwgiz.mavenShadePlugin.log4j2CacheTransformer.PluginsCacheFileTransformer">
            </transformer>
          </transformers>
        </configuration>
      </execution>
    </executions>
    <dependencies>
      <dependency>
        <groupId>com.github.edwgiz</groupId>
        <artifactId>maven-shade-plugin.log4j2-cachefile-transformer</artifactId>
        <version>2.11.0</version>
      </dependency>
    </dependencies>
  </plugin>
</plugins>
```

A number of the transformer version (it's 2.11.0 now) corresponds to the version of log4j2 (which is a dependency of this plugin)

It might work with newer/older versions of log4j2 but if you want to be sure then fork/download this repository and change the log4j2 dependencies