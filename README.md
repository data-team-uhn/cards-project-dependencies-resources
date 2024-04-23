# CARDS (Clinical Archive for Data Science) - Project Dependencies Resources

This repository contains resource files needed for building a list of feature dependencies for CARDS-based projects.
Since SLING feature files cannot list other features as dependencies, just plain jars, all feature dependencies must be explicitly listed when starting Sling.
For convenience, a CARDS-based project lists its feature dependencies in a special file both when starting it as a Docker container and using the `start.sh` script.
To avoid code duplication, the dependencies are declared only once in the project's root POM file, and two separate files are generated at build time.

This works as a Maven Remote Resources bundle.
The `maven-remote-resources-plugin` is used to build this module as a remote resources bundle,
listing the two source files as remote resources.
Then, when building a CARDS-based project,
it is used to generate resources that are included in the resulting artifact.
These source files are interpreted as Velocity scripts,
with information about the project available as scripting variables.

## Prerequisites:
* Java 11
* Maven 3.3+

## Build:
`mvn clean install`
