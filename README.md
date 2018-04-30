
pl.kubiczak.felix.shark.parent
==============================

[![Build Status](https://travis-ci.org/wiiitek/pl.kubiczak.felix.shark.parent.svg?branch=master)](https://travis-ci.org/wiiitek/pl.kubiczak.felix.shark.parent)


This project manages properties and plugins versions for other projects with

    <groupId>pl.kubiczak.felix.shark</groupId>

Project site available at [https://shark.kubiczak.pl/][project-site]

Maven artifacts at [http://maven.kubiczak.pl/pl/kubiczak/felix/shark/][custom-maven-repo]

Release instructions
--------------------


### Parent module

```
mvn release:prepare -B -N -Darguments="-N" -DreleaseVersion=1.2 -DdevelopmentVersion=1.3-SNAPSHOT
mvn release:perform -B -N -Darguments="-N -Dgpg.keyname=01D2F996" -Psign,release 
```


### Submodules

Submodules of this project are versioned in separate GIT repositories.
They are released independently.

```
mvn release:prepare -B -DreleaseVersion=1.2 -DdevelopmentVersion=1.3-SNAPSHOT 
mvn release:perform -B -Darguments="-Dgpg.keyname=01D2F996" -Psign,release
```

### Details

#### -N and -Darguments

Parent module and submodules are released independently.
Therefore during parent module release we need to use `-N` (non-recursive) flag.
This will run Maven Release Plugin for parent module only.
We don't want to run release plugin for all submodules at this time.

But as described in [Maven Release Plugin FAQ][maven-release-plugin-faq]
for release plugin we need to use:

    mvn -N -Darguments=-N

#### Release profile

Release profile adds javadoc and sources artifacts:

    -Prelease

#### Sign profile

`sign` profile requires [gpg2][gpg2] installed and gpg key id:

    -Psign -Dgpg.keyname=9A105524

#### Non-interactive release

In order to perform [non-interactive][maven-release-plugin-non-interative] release we use:

    -B -DreleaseVersion=1.2 -DdevelopmentVersion=1.3-SNAPSHOT

License
-------

[![CC BY-NC 4.0](https://licensebuttons.net/l/by-nc/4.0/88x31.png "Attribution-NonCommercial 4.0 International")][license]

[Attribution-NonCommercial 4.0 International][license]


Plugins versions
---------------------

Available Maven plugins upgrades are reported in:

* `src/main/resources/plugins-report.txt`

[license]: http://creativecommons.org/licenses/by-nc/4.0/
[project-site]: https://shark.kubiczak.pl/
[custom-maven-repo]: http://maven.kubiczak.pl/pl/kubiczak/felix/shark/
[maven-release-plugin-faq]: http://maven.apache.org/maven-release/maven-release-plugin/faq.html#nonrecursive
[maven-release-plugin-non-interative]: http://maven.apache.org/maven-release/maven-release-plugin/examples/non-interactive-release.html
[gpg2]: https://www.gnupg.org/
