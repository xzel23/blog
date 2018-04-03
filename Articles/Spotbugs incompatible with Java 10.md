# Spotbugs incompatible with Java 10

Spotbugs is currently [incompatible with Java 10](https://github.com/spotbugs/spotbugs/issues/593). This will be fixed in the upcoming Version 4 of Spotbugs, and possibly in also an upcoming 3.1.x version of this tool as the patch has already been merged.

In case you also have JDK 9 installed, you may want to set `JAVA_HOME` to the JDK 9 version. If working with gradle and you don't want to change `JAVA_HOME`, you have [several choices](https://stackoverflow.com/questions/18487406/how-do-i-tell-gradle-to-use-specific-jdk-version?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa):

 * in `gradle.properties`, either in the `.gradle` directory in your home directory or the project directory, set `org.gradle.java.home=/path_to_jdk_directory`
 
 * in your `build.gradle`:
    
    compileJava.options.fork = true
    compileJava.options.forkOptions.executable = /path_to_javac

 * pass the path to the gradle wrapper on the command line:
   
    ./gradlew -Dorg.gradle.java.home=/path_to_jdk_directory
   
