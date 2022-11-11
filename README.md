# Tools_Data

# OracleTracker

This project place probes after the instantiation of exceptions in source code and test code.

To generate the jar file, run

```
mvn clean compile assembly:single test-compile
```

change the probe info in visitMethodInsn method in Oraclevisitor to distinguish probes for source code from probes for test code.

To instrument the project source code's bytecode

```
java -jar "XXXX.jar" target/classes
```

PIT configuration(change something in <scope> and <systemPath>
```
      <plugin>
        <groupId>org.pitest</groupId>
        <artifactId>pitest-maven</artifactId>
        <version>1.8.0 </version>
        <configuration>
          <fullMutationMatrix>true</fullMutationMatrix>
          <outputFormats>
            <outputFormat>XML</outputFormat>
            <outputFormat>HTML</outputFormat>
          </outputFormats>
          <exportLineCoverage>true</exportLineCoverage>
          <!--We want each report to override the former one-->
          <timestampedReports>false</timestampedReports>
          <verbose>true</verbose>
          <detail>true</detail>
        </configuration>
      </plugin>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <configuration>
          <source>8</source>
          <target>8</target>
        </configuration>
      </plugin>
      <plugin>
        <groupId>org.pitest</groupId>
        <artifactId>pitest-maven</artifactId>
        <!-- <version>LATEST</version> -->
        <version>1.0.0-SNAPSHOT</version>

        <!--                <scope>system</scope>-->
        <!--                <systemPath>/Users/superhang/Documents/ResearchExperiment/pitest-master/pitest/target/pitest-1.0.0-SNAPSHOT.jar</systemPath>-->
        <dependencies>
          <!--                    <dependency>-->
          <!--                        <groupId>org.pitest</groupId>-->
          <!--                        <artifactId>pitest-junit5-plugin</artifactId>-->
          <!--                        &lt;!&ndash; <version>0.15</version> &ndash;&gt;-->
          <!--                        <version>1.1.0</version>-->
          <!--                    </dependency>-->
          <dependency>
            <groupId>org.pitest</groupId>
            <artifactId>pitest</artifactId>
            <version>1.0.0-SNAPSHOT</version>
          </dependency>
          <dependency>
            <groupId>org.pitest</groupId>
            <artifactId>pitest-entry</artifactId>
            <version>1.0.0-SNAPSHOT</version>
          </dependency>
          <dependency>
            <groupId>org.pitest</groupId>
            <artifactId>pitest-html-report</artifactId>
            <version>1.0.0-SNAPSHOT</version>
          </dependency>
        </dependencies>
        <configuration>
          <verbose>true</verbose>
          <failWhenNoMutations>false</failWhenNoMutations>
          <timestampedReports>false</timestampedReports>
          <fullMutationMatrix>true</fullMutationMatrix>
          
          <!-- <junit5PluginVersion>0.15</junit5PluginVersion> -->
          <!--                    <junit5PluginVersion>1.1.0</junit5PluginVersion>-->
          <!--                    &lt;!&ndash; <pitClasspath>pitest.path</pitClasspath> &ndash;&gt;-->
          <!--                    <targetClasses>-->
          <!--                        <param>org.jsoup.parser.CharacterReader</param>-->
          <!--                    </targetClasses>-->
          <!--                    &lt;!&ndash; <maxMutationsPerClass>10</maxMutationsPerClass> &ndash;&gt;-->
          <!--                    <features>+CLASSLIMIT(limit[10])</features>-->
        </configuration>
      </plugin>
```

