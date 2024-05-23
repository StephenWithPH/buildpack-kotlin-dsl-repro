## What

Demonstration of :( behavior when `google.java.functions-framework` builder encounters Gradle's Kotlin DSL.

## How
### See it work with Gradle Groovy DSL
From branch `main`: 

```sh
pack build \
  --builder gcr.io/buildpacks/builder:latest \
  --env GOOGLE_FUNCTION_TARGET="org.example.App" \
  --env GOOGLE_RUNTIME_VERSION="21" \
  repro
```

`pack` should build successfully.

### See it fail with Gradle Kotlin DSL
From branch `convert-to-kotlin-dsl`:

```sh
pack build \
  --builder gcr.io/buildpacks/builder:latest \
  --env GOOGLE_FUNCTION_TARGET="org.example.App" \
  --env GOOGLE_RUNTIME_VERSION="21" \
  repro
```

`pack` should fail with:

```
[builder] === Java - Functions Framework (google.java.functions-framework@1.1.0) ===
[builder] --------------------------------------------------------------------------------
[builder] failed to build: (error ID: e371563c):
[builder] function has neither pom.xml nor already-built jar file; directory has these entries: .git, .gitattributes, .github, .gitignore, .gradle, build, build.gradle.kts, gradle, gradlew, gradlew.bat, settings.gradle.kts, src
```
