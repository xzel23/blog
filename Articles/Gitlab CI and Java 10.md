Gitlab CI and Java 10
=====================

After having my builds fail for quite some time since updating to JDK 10 (and not finding enough time to create an image myself), I finally found a working [docker image](https://hub.docker.com/r/goodforgod/debian-jdk10-oracle/) with JDKK 10 and JavaFx.

To use it in Gitlab CI:

    image: goodforgod/debian-jdk10-oracle

