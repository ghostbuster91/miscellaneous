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

1. BSP - Builder server protocol made by JetBrains. Code editor needs to be aware of e.g. what the classpath is and so on in order to run tests or main application. This protocol allows to comunicate between code editor and a build tool, so the build tools' specific integrations don't have to be build into code editors and repeated. 
2. LSP - Language server protocol made by Microsoft for Visual Studio code. Extract language/framework specific stuff out from the code editor to make it ligher and also to reuse language support acros all code editors which support LSP. This doesn't overlap with BSP - it is used for code navigation, syntax highlithing etc.
3. zinc - scala incremental compiler. Many build tools which want to be fast need to implement integration layer with it.
4. bloop - Bloop is a build server that runs in the backgroud of your machine and serves build requests for a specific workspace. It uses BSP to communicate with IDE and various build tools. It implements the integration layer for zinc, so the build tools don't have to. With this in your toolbelt the build tool is only responsible for parsing the build definition and fetching dependencies.
5. semanticDB
6. coursier - coursier is a dependency resolver / fetcher à la Maven / Ivy, entirely rewritten from scratch in Scala. It aims at being fast and easy to embed in other contexts. Its core embraces functional programming principles.

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

