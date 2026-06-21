# Day 43 - Resources

## Tools Used
- Apache Maven
- Java JDK (required for Maven)

## Commands Reference
| Purpose | Command |
|---|---|
| Check Maven version | `mvn -version` |
| Generate new project | `mvn archetype:generate -DgroupId=<g> -DartifactId=<a> -DarchetypeArtifactId=maven-archetype-quickstart` |
| Compile | `mvn compile` |
| Run tests | `mvn test` |
| Package | `mvn package` |
| Install to local repo | `mvn install` |
| Clean build artifacts | `mvn clean` |
| Clean + full build | `mvn clean install` |

## Key Terms Glossary
- **pom.xml**: Project Object Model, Maven's central config file
- **Build Lifecycle**: defined sequence of build phases (validate -> compile -> test -> package -> verify -> install -> deploy)
- **Maven Central**: the default public repository Maven pulls dependencies from
- **Transitive Dependency**: a dependency of a dependency, automatically resolved by Maven

## Further Reading
- Maven official documentation (maven.apache.org)
- Maven Central Repository (search.maven.org) - browse available dependencies

## Skills Gained Today
- Maven project structure and pom.xml configuration
- Build lifecycle command usage
- Dependency management understanding
- Plugin configuration basics
