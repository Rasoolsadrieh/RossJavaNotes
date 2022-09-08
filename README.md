# Maven

## Overview

-   Project Management Tool
-   Opinionated
-   Build automation
-   dependency management
    -   from within organization
    -   open source world as well
-   Primary Goals:
    -   Making the build proces easy
    -   Providing a uniform build system
    -   Providing quality project practices
    -   Encourgaging better development practices
-   Convention over configuration
-   Provides a common interface
-   Maven has a repository where it puts all it's packages and plugin on the fly
-   Many companies maintain their own repositories
-   Lightweight

## Maven Build Lifecycle

-   When Maven builds your project, it goes through several steps called **phases**. The default maven build lifecycle goes through the following phases:

    1. Validate => project is correct and all necessary information is available
    2. Compile => compiles project source code
    3. Test => tests all compiled code
    4. Package => packages all compiled code to WAR/JAR file
    5. Integration => performs all integration tests on WAR/JAR
    6. Verify => runs checks on the results of integration tests
    7. Install => installs WAR/JAR to local repository
    8. Deploy => copies final WAR/JAR to the remote repository

-   Each phase in turn is composed of plugin goals that are bound to zero or more build phases. A "goal" represents a specific task which contributes to the building or managing of the project.

For more information, see the [Maven documentation](https://maven.apache.org/guides/introduction/introduction-to-the-lifecycle.html).

## Using the `mvn` command

-To use the Maven CLI (command-line interface), first test that you have Maven installed:

```bash
mvn --version
mvn -v
```

-Now, once you are in your project directory, you can run any phase in the default build lifecycle. Maven will look for the `pom.xml` file and use that to run the phase.

```bash
cd /path/to/myproject/
mvn package
```

-To execute a specific Maven goal, use the `plugin:goal` syntax:

```bash
mvn dependency:copy-dependencies
```

-   Multiple phases or goals can be run sequentially. Again, see the Maven documentation for more information.

## Maven Repository Locations

-   When **Maven "builds"** a Java project

    -   it must first search for any dependencies declared in the `pom.xml` file.
    -   Maven dependencies are stored both **locally** and in a **central repository**.
        -   **Local** repository is in the `$HOME/.m2/repository` folder
            -   (can be changed in `$MAVEN_HOME/conf/settings.xml`)
        -   **Cental** repository is accessible at [https://mvnrepository.com](https://mvnrepository.com).
            -   If Maven cannot find a given dependency locally, it searches the central repository for the artifact and then downloads it to the local repository.

-   Maven "build"
    -   Take project source code
    -   along with any dependencies like libraries or frameworks
    -   compile it
    -   bundle it all together into an artifact
        -   either a `.war` file
            -   WAR stands for "web archive"
        -   a `.jar` file
            -   JAR stands for "Java archive"
        -   an `.ear` file
            -   EAR stands for "Enterprise Application archive"
        -   This artifact can then be either directly run or deployed onto a web container (in the case of a web application).

# POM - Project Object Model

-   [Maven](https://maven.apache.org/) is a dependency manager and build automation tool for Java programs.
-   Maven project configuration and dependencies are handled via the **Project Object Model**,

    -   defined in the `pom.xml` file.
    -   This file contains information about the project used to build the project
    -   includes project dependencies and plugins

-   Some other important tags within the `pom.xml` file include:

-   `<project>`
    -   this is the root tag of the file
-   `<modelVersion>`
    -   defining which version of the page object model to be used
-   `<name>`
    -   name of the project
-   `<properties>`
    -   project-specific settings
-   `<dependencies>`
    -   this is where you put your Java dependencies you want to use.
    -   Each one needs a `<dependency>`, which has:
        -   `<groupId>`
        -   `<artifactId`
        -   `<version>`
        -   Thse make up the [project coordinates](#maven-project-coordinates)
-   `<plugins>` - for 3rd party plugins that work with Maven

Here's an example:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>

  <groupId>com.revature.app</groupId>
  <artifactId>my-app</artifactId>
  <version>1</version>

  <dependencies>
    <dependency>
      <groupId>org.apache.maven</groupId>
      <artifactId>maven-artifact</artifactId>
      <version>${mavenVersion}</version>
    </dependency>
    <dependency>
      <groupId>org.apache.maven</groupId>
      <artifactId>maven-core</artifactId>
      <version>${mavenVersion}</version>
    </dependency>
  </dependencies>

</project>
```

## Maven Project Coordinates

-   Maven Project coordinates identify uniquely a project, a dependency, or a plugins defined in the `pom.xml` file these are:
    -   `group-id`
        -   The group, company, team, organization, project, or other group. for example: "com.revature"
    -   `artifact-id`
    -   A unique identifier under `groupId` that represents a single project. for example: "myproject"
    -   `version`
    -   A specific release of a project.
    -   Projects that have been released have a fixed version identifier that refers to a specific version of the project.
    -   Projects undergoing active development can use a special identifier that marks a version as a `SNAPSHOT`. for example: "0.0.1-SNAPSHOT"
-   `packaging`
    -   The type of project, defaulting to `jar`, describing the packaged output produced by a project.
        -   A project with packaging `jar` produces a JAR archive
        -   a project with packaging `war` produces a web application
