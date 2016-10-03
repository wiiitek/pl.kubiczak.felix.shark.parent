
pl.kubiczak.felix.shark.parent
==============================

[![Build Status](https://travis-ci.org/wiiitek/pl.kubiczak.felix.shark.parent.svg?branch=master)](https://travis-ci.org/wiiitek/pl.kubiczak.felix.shark.parent)


This project manages properties and plugins versions for other projects with

    <groupId>pl.kubiczak.felix.shark</groupId>

Project site available at [https://shark.kubiczak.pl/][project-site]

Maven artifacts at [http://maven.kubiczak.pl/pl/kubiczak/felix/shark/][custom-maven-repo]

Release instructions
--------------------

Submodules of parent project are within separate GIT repositories.
Therefore during release we need to use `-N -Darguments=-N` (non-recursive) arguments
as described at [Maven Release Plugin FAQ][maven-release-plugin-faq]:

    mvn -N -Darguments=-N

Please remember about using release profile:

    -P release

In order to perform [non-interactive][maven-release-plugin-non-interative] release use:

    -B -DreleaseVersion=1.2 -DdevelopmentVersion=1.3-SNAPSHOT

To sum it up, release may be performed with following commands:

    mvn release:prepare -B -DreleaseVersion=1.2 -DdevelopmentVersion=1.3-SNAPSHOT -P release
    mvn release:perform -B -P release

License
-------

![CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/88x31.png "Attribution-NonCommercial 4.0 International")

[Attribution-NonCommercial 4.0 International][license]


Plugins versions
---------------------

Plugins and dependencies versions are reported with every build in:

* `src/main/resources/plugins-report.txt`

[license]: http://creativecommons.org/licenses/by-nc/4.0/
[project-site]: https://shark.kubiczak.pl/
[custom-maven-repo]: http://maven.kubiczak.pl/pl/kubiczak/felix/shark/
[maven-release-plugin-faq]: http://maven.apache.org/maven-release/maven-release-plugin/faq.html#nonrecursive
[maven-release-plugin-non-interative]: http://maven.apache.org/maven-release/maven-release-plugin/examples/non-interactive-release.html
