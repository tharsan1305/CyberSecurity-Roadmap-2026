# Day 43 - Lab: Maven Project Build

## Task 1: Install Maven
```bash
sudo apt install maven -y
mvn -version
```

## Task 2: Generate a New Maven Project
```bash
mvn archetype:generate -DgroupId=com.example -DartifactId=my-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
cd my-app
```

## Task 3: Explore Generated Structure
```bash
find . -type f
cat pom.xml
```
Note the standard Maven directory layout: `src/main/java`, `src/test/java`.

## Task 4: Build and Test the Project
```bash
mvn compile
mvn test
mvn package
ls target/
```
Record: did the build succeed, and what file was produced in `target/`?

## Task 5: Add a Dependency and Rebuild
Edit `pom.xml` to add a dependency (e.g., a small utility library), then:
```bash
mvn clean install
```
Confirm Maven downloaded the new dependency automatically.

## Results
| Item | Value |
|---|---|
| Maven installed (Y/N) | |
| Project generated (Y/N) | |
| Build succeeded (Y/N) | |
| JAR file produced in target/ (Y/N) | |
| New dependency downloaded successfully (Y/N) | |

## Screenshots
```
![Maven Project Structure](Screenshots/maven-structure.png)
![Build Output](Screenshots/build-output.png)
```

## Lab Summary
Note how Maven automatically resolved dependencies without manual downloading, and how the build lifecycle phases ran in sequence.
