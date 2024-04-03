# openapi-generator-bug

Minimal reproducible example for [[BUG] On openapi-generator-maven-plugin v7.3.0 with interfaceOnly uses ApiUtil but does not generate it](https://github.com/OpenAPITools/openapi-generator/issues/17965).

## Development

This repo is aimed to be opened in **[VSCode](https://code.visualstudio.com/)** with the **[Remote Development](https://code.visualstudio.com/docs/remote/remote-overview)** extension pack installed.

The development is done inside a **[Docker container](https://docker.com/)** that installs and configures the required tools on first run (the first time the Docker image is build might take some time).

Please, make sure you have **VSCode** with the **Remote Development extension pack** and **Docker** installed and working on your system before cloning the respository then clone de repository:

`git clone https://github.com/rubensa/openapi-generator-bug.git`

For detailed instructions see: **[Developing inside a Container](https://code.visualstudio.com/docs/remote/containers)**.

## Project Organization

    ├── .devcontainer     <- VSCode Remote Development configuration
    │
    ├── src               <- Application source code
    │
    ├── .gitgnore         <- Git ignored files
    ├── pom.xml           <- Maven dependencies
    └── README.md         <- This file

## Showing the bug

You can see the bug by running the following command in a terminal inside the VSCode container:
```shell script
mvn clean compile
```

This will generate under **target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/** folder the Java classes based on **src/main/resources/META-INF/resources/open-api/sample.yml** OpenAPI definition file before trying to compile the project.

The error will be shown in the terminal:

```shell script
[INFO] Scanning for projects...
[INFO] 
[INFO] ----------------< org.eu.rubensa:openapi-generator-bug >----------------
[INFO] Building openapi-generator-bug 0.0.1-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.3.2:clean (default-clean) @ openapi-generator-bug ---
[INFO] Deleting /workspaces/openapi-generator-bug/target
[INFO] 
[INFO] --- build-helper:3.5.0:add-source (add-source) @ openapi-generator-bug ---
[INFO] Source directory: /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java added.
[INFO] 
[INFO] --- openapi-generator:7.4.0:generate (default) @ openapi-generator-bug ---
[INFO] Generating with dryRun=false
[INFO] Output directory (/workspaces/openapi-generator-bug/target/generated-sources/openapi) does not exist, or is inaccessible. No file (.openapi-generator-ignore) will be evaluated.
[INFO] OpenAPI Generator: spring (server)
[INFO] Generator 'spring' is considered stable.
[INFO] ----------------------------------
[INFO] Environment variable JAVA_POST_PROCESS_FILE not defined so the Java code may not be properly formatted. To define it, try 'export JAVA_POST_PROCESS_FILE="/usr/local/bin/clang-format -i"' (Linux/Mac)
[INFO] NOTE: To enable file post-processing, 'enablePostProcessFile' must be set to `true` (--enable-post-process-file for CLI).
[INFO] Invoker Package Name, originally not set, is now derived from api package name: org.eu.rubensa.openapi
[INFO] Processing operation setSample
[INFO] writing file /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/model/Problem.java
[INFO] writing file /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/model/Sample.java
[INFO] Update operation [setSample]. Remove header [prefer] because it's marked to be implicit
[INFO] writing file /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java
[INFO] Skipping generation of Webhooks.
[INFO] Skipping generation of supporting files.
################################################################################
# Thanks for using OpenAPI Generator.                                          #
# Please consider donation to help us maintain this project 🙏                 #
# https://opencollective.com/openapi_generator/donate                          #
################################################################################
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ openapi-generator-bug ---
[INFO] Copying 1 resource from src/main/resources to target/classes
[INFO] Copying 7 resources from src/main/resources to target/classes
[INFO] 
[INFO] --- compiler:3.11.0:compile (default-compile) @ openapi-generator-bug ---
[INFO] Changes detected - recompiling the module! :source
[INFO] Compiling 4 source files with javac [debug release 21] to target/classes
[INFO] -------------------------------------------------------------
[ERROR] COMPILATION ERROR : 
[INFO] -------------------------------------------------------------
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[108,21] cannot find symbol
  symbol:   variable ApiUtil
  location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[113,21] cannot find symbol
  symbol:   variable ApiUtil
  location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[118,21] cannot find symbol
  symbol:   variable ApiUtil
  location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[123,21] cannot find symbol
  symbol:   variable ApiUtil
  location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[128,21] cannot find symbol
  symbol:   variable ApiUtil
  location: interface org.eu.rubensa.openapi.api.SampleApi
[INFO] 5 errors 
[INFO] -------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.651 s
[INFO] Finished at: 2024-04-03T11:28:37Z
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.11.0:compile (default-compile) on project openapi-generator-bug: Compilation failure: Compilation failure: 
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[108,21] cannot find symbol
[ERROR]   symbol:   variable ApiUtil
[ERROR]   location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[113,21] cannot find symbol
[ERROR]   symbol:   variable ApiUtil
[ERROR]   location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[118,21] cannot find symbol
[ERROR]   symbol:   variable ApiUtil
[ERROR]   location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[123,21] cannot find symbol
[ERROR]   symbol:   variable ApiUtil
[ERROR]   location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java:[128,21] cannot find symbol
[ERROR]   symbol:   variable ApiUtil
[ERROR]   location: interface org.eu.rubensa.openapi.api.SampleApi
[ERROR] -> [Help 1]
[ERROR] 
[ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[ERROR] Re-run Maven using the -X switch to enable full debug logging.
[ERROR] 
[ERROR] For more information about the errors and possible solutions, please read the following articles:
[ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoFailureException
```

If you modify the `pom.xml` file and change the `openapi-generator-maven-plugin` version to `7.2.0` the error will not happen.

```shell script
[INFO] Scanning for projects...
[INFO] 
[INFO] ----------------< org.eu.rubensa:openapi-generator-bug >----------------
[INFO] Building openapi-generator-bug 0.0.1-SNAPSHOT
[INFO]   from pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.3.2:clean (default-clean) @ openapi-generator-bug ---
[INFO] Deleting /workspaces/openapi-generator-bug/target
[INFO] 
[INFO] --- build-helper:3.5.0:add-source (add-source) @ openapi-generator-bug ---
[INFO] Source directory: /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java added.
[INFO] 
[INFO] --- openapi-generator:7.2.0:generate (default) @ openapi-generator-bug ---
[INFO] Generating with dryRun=false
[INFO] Output directory (/workspaces/openapi-generator-bug/target/generated-sources/openapi) does not exist, or is inaccessible. No file (.openapi-generator-ignore) will be evaluated.
[INFO] OpenAPI Generator: spring (server)
[INFO] Generator 'spring' is considered stable.
[INFO] ----------------------------------
[INFO] Environment variable JAVA_POST_PROCESS_FILE not defined so the Java code may not be properly formatted. To define it, try 'export JAVA_POST_PROCESS_FILE="/usr/local/bin/clang-format -i"' (Linux/Mac)
[INFO] NOTE: To enable file post-processing, 'enablePostProcessFile' must be set to `true` (--enable-post-process-file for CLI).
[INFO] Invoker Package Name, originally not set, is now derived from api package name: org.eu.rubensa.openapi
[INFO] Processing operation setSample
[INFO] writing file /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/model/Problem.java
[INFO] writing file /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/model/Sample.java
[INFO] Update operation [setSample]. Remove header [prefer] because it's marked to be implicit
[INFO] writing file /workspaces/openapi-generator-bug/target/generated-sources/openapi/src/main/java/org/eu/rubensa/openapi/api/SampleApi.java
[INFO] Skipping generation of Webhooks.
[INFO] Skipping generation of supporting files.
################################################################################
# Thanks for using OpenAPI Generator.                                          #
# Please consider donation to help us maintain this project 🙏                 #
# https://opencollective.com/openapi_generator/donate                          #
################################################################################
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ openapi-generator-bug ---
[INFO] Copying 1 resource from src/main/resources to target/classes
[INFO] Copying 7 resources from src/main/resources to target/classes
[INFO] 
[INFO] --- compiler:3.11.0:compile (default-compile) @ openapi-generator-bug ---
[INFO] Changes detected - recompiling the module! :source
[INFO] Compiling 4 source files with javac [debug release 21] to target/classes
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  2.756 s
[INFO] Finished at: 2024-04-03T11:30:17Z
[INFO] ------------------------------------------------------------------------
```