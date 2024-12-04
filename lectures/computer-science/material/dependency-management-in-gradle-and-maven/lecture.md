# Dependency Management in Gradle and Maven

## Maven

Maven uses an XML file for dependency management, named `pom.xml`. To add a dependency, you'll have to specify its groupId, artifactId, and version.

```xml
<dependencies>
  <dependency>
    <groupId>junit</groupId>
    <artifactId>junit</artifactId>
    <version>4.12</version>
    <scope>test</scope>
  </dependency>
</dependencies>
```
Maven also supports dependency scopes (compile, provided, runtime, test, system, import) to control the visibility of your dependencies.

## Gradle

Gradle, on the other hand, uses a Groovy-based DSL for its configuration. To declare a dependency, you add it to the appropriate dependency configuration in the `build.gradle` file.

```groovy
dependencies {
  implementation 'com.google.guava:guava:28.2-jre'
  testImplementation 'junit:junit:4.12'
}
```
In Gradle, the keywords `implementation`, `api`, `compileOnly`, and `runtimeOnly` are used as dependency configurations.

## Transitive Dependencies

Both Maven and Gradle handle transitive dependencies (dependencies of your direct dependencies). If multiple versions of a dependency are found, they use conflict resolution strategies to choose one.

Maven uses a "nearest definition" strategy which means that it uses the version of the closest dependency to your project in the tree of dependencies. You can override this by defining a `dependencyManagement` section in your POM file.

Gradle, by default, uses a strategy where it picks the newest version of the dependency. You can customize this strategy by configuring the `resolutionStrategy` in your `build.gradle` file.

```groovy
configurations.all {
  resolutionStrategy {
    force 'com.google.guava:guava:27.1-jre'
  }
}
```
In this example, Gradle will always use Guava version 27.1-jre, even if a newer version is declared elsewhere.