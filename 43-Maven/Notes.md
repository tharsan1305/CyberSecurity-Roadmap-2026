# Day 43 - Maven

## Goal
Learn Maven - a build automation and dependency management tool for Java projects, commonly seen in CI/CD pipelines (Jenkins integration comes next, Topic 44).

---

## 1. Project Object Model (POM.xml)

Maven's central configuration file defines project metadata, dependencies, build settings.

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>my-app</artifactId>
  <version>1.0.0</version>
  <packaging>jar</packaging>

  <dependencies>
    <dependency>
      <groupId>junit</groupId>
      <artifactId>junit</artifactId>
      <version>4.13.2</version>
      <scope>test</scope>
    </dependency>
  </dependencies>
</project>
```

## 2. Build Lifecycle

Maven follows a defined sequence of phases - running a later phase automatically runs all earlier ones.

```
validate -> compile -> test -> package -> verify -> install -> deploy
```

Common commands:
```bash
mvn compile        # compiles source code
mvn test             # runs tests
mvn package           # packages into JAR/WAR
mvn install             # installs to local repository
mvn clean               # removes previous build artifacts
mvn clean install         # common combination: clean then full build
```

## 3. Dependency Management

Maven automatically downloads dependencies (and their transitive dependencies) from repositories (Maven Central by default) based on what's declared in `pom.xml` - no manual JAR file management needed.

```xml
<dependency>
  <groupId>org.springframework</groupId>
  <artifactId>spring-core</artifactId>
  <version>5.3.20</version>
</dependency>
```

Security relevance: outdated/vulnerable dependencies are a major attack vector (this connects directly to dependency scanning in DevSecOps, Topic 51, and the broader OWASP "Vulnerable Components" category).

## 4. Plugins

Plugins extend Maven's functionality beyond the default lifecycle - e.g., code coverage, static analysis, packaging formats.

```xml
<build>
  <plugins>
    <plugin>
      <groupId>org.apache.maven.plugins</groupId>
      <artifactId>maven-compiler-plugin</artifactId>
      <version>3.10.1</version>
      <configuration>
        <source>17</source>
        <target>17</target>
      </configuration>
    </plugin>
  </plugins>
</build>
```

---

## Interview Questions

**Q1. What is the purpose of pom.xml?**
It's Maven's central configuration file, defining project metadata, dependencies, plugins, and build settings.

**Q2. What does `mvn clean install` do?**
`clean` removes previous build artifacts; `install` runs the full build lifecycle and installs the resulting package to the local Maven repository.

**Q3. Why does Maven's dependency management matter for security?**
Outdated or vulnerable third-party dependencies are a major source of real-world vulnerabilities; Maven's dependency declarations make it possible to scan and audit them systematically.

**Q4. What is a Maven plugin?**
Code that extends Maven's build process beyond the default lifecycle phases, such as compilation settings, code analysis, or packaging customization.

## Key Takeaways
- Learned pom.xml structure and purpose
- Learned Maven's build lifecycle phases and common commands
- Learned dependency management and its security relevance
- Learned plugin usage for extending build functionality
