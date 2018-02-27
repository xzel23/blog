# Gradle

The Gralde build tool can either be used through a local installation on the developper machine or as a wrapper installed under the project structure.

## The Gradle Wrapper

The Gradle Wrapper is a version of Gradle that is installed locally inside the project directory. It makes sure that the build will be executed by the correct version of gradle.

### Install The gradle Wrapper

1. Change to the project directory.
2. Install the wrapper
    ```
    gradle wrapper --gradle-version 4.4.1
    ```

### Update the Gradle Wrapper

1. Change into the project directory
2. Run the `wrapper` task through the currently installed wrapper:
    ```
    ./gradlew wrapper --gradle-version 4.4.1
    ```