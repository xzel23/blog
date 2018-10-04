# Moving on to JDK 11: Upgrading to JUnit 5

After changing the target release of my projects to Java 5, and resolving all issues related to the module path, what else could go wrong? Well, I don't know why, but JUnit complained that the "super class name is empty" and wouldn't even start a single test. I don't know if it's a problem with JUnit and JDK 11 in general or related to my projects using the module path instead of the class path, but it simply didn't work.

Instead of putting too much work into this, I thought it might as well be worth upgrading to JUnit 5 and see if the problems persist.

Here's my experience, and I hope it might be of help to some.

## Change Gradle dependencies

Change JUnit dependencies to use JUnit 5 iinstead of JUnit 4:

	dependencies {
		...	
	    // JUnit
	    def junitVersion = "5.3.1"
	    testImplementation "org.junit.jupiter:junit-jupiter-api:${junitVersion}"
	    testRuntimeOnly "org.junit.jupiter:junit-jupiter-engine:${junitVersion}"
	}

## Move tests to a test package

Since it's not possible to have your tests in the same packages as the classes under test anymore without extra hacks (if you use Maven, it will do this for you), and I concentrate on testing the publich API anyway (whitebox test), I moved all my test code to a new test package.

So the package declaration changes from:

    package foo.bar;

to this:

    package foo.bar.test;
    
    import foo.bar.*;

## Create a module-info.java for the test
 
I'm assuming the typical Gradle project layout with sources in `src/main/java` and test sources in `src/test/java` here. You should already have `src/main/java/module-info.java`. Now create `src/test/java/module-info.java` like in this example:

	module foo.bar.test {
	    requires foo.bar;
	    requires org.junit.jupiter.api;
	    // other modules needed by test code
	}

## Change the import statements

JUnit 5 package structure has changed and so the import statements have to be changed correspondingly:
 
    import static org.junit.jupiter.api.Assertions.*;
    import org.junit.jupiter.api.Test;
 
## Change your test code according to API changes

Here is a short and incomplete list of things I noticed while making the switch to JUnit 5:

 - The argument order of `assertXYZ` methods that take a message argument changed. While in JUnit 4, the message argument came first, it was moved to the end of the parameter list in JUnit 5.
 
 - The double version of `assertEquals()` expects the `eps` parameter to be positive. This is a corner case because I have some cases where I test doubles for exact equality (because they are known to contain integral values), and in those cases I passed `0.0` as tolerance. So I had to replace `assertEquals(a, b, 0.0)` with `assertEquals(a, b, Double.MIN_VALUE)`.

 I will add other things to this list when I find more.
 