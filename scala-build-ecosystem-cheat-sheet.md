# Scala build ecosystem cheet sheet


## Build tools

1. sbt - Official scala build tool. It is the most popular, very matured and has comperhensive documentation. 
  There is also a ton of stuff build on top of it (plugins, integrations etc.). Some people find it hard to grasp.
3. mill - Build tool initially created by Li Haoyi. Strives to be simpler than sbt.
4. furry - Build tool created by Jon Pretty. Build definition separated from source code. Imperative approach to edition and maintenance.

## IDE

1. Intelij IDEA
2. VS code + metals -> 
3. Ensime - ???

## Under the hood

1. BSP
2. LSP
3. zin
4. bloop
5. semanticDB
6. coursier

## Linters & formatters
1. scalafmt
2. scalari
3. scalafix
4. scalastyle

## sbt-plugins
(apart from linters and formatters)
1. sbt-native-pacakger - various ways of packaging your application. Usually used for creation of docker images.
2. sbt-assembly - packages your application as a fat jar
3. sbt-ci-release
4. sbt-release
5. sbt-git - calling git from sbt. Used by sbt-ci-release
6. sbt-tpolecat - recommended set of compiler flags
7. sbt-dynver
8. sbt-pgp - calling pgp binary from sbt
9. sbt-travis-ci
10. sbt-github-actions

## github actions
1. [coursier-cache-action](https://github.com/coursier/cache-action) - A GitHub action to save / restore the coursier / sbt / mill / Ammonite caches of your build.

