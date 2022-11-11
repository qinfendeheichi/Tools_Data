# Tools_Data

# OracleTracker

This project place probes after the instantiation of exceptions in source code and test code.

To generate the jar file, run

```
mvn clean compile assembly:single test-compile
```

change the probe info in visitMethodInsn method in Oraclevisitor to distinguish probes for source code from probes for test code.

To instrument the project source code's bytecode(for maven projects)

```
java -jar "XXXX.jar" target/classes
```

# Modified PIT

For PIT: We choose to report the exception type, lineNumber, FileName, and MethodName on the scene.
We also chose to make some modification in org/pitest/testapi/execute/Pitest.java where we know the test start before it really starts in execution.


Running mutation analysis with "FullMutationMatrix" and "Verbose" mode. The detailed test exceuction inforamtion can be directed to standard error.


# Data
Data1-5 and 6-10 have 10 csv files which contain test run information for all covered mutants labeled as "KILLED" or "SURVIVED" by PIT.
