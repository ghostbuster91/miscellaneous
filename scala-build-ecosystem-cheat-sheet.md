# Scala build ecosystem cheat sheet

## Introduction
Scala struggled for many years to provide great developer experience. Thankfully to the great work of many contributors around the world these times are gone forever. Standard ways of enriching IDE's with language specific things were not enough. That's why scala had to take the lead in driving the shape of the build systems further. Below is an incomplete list of tools somehow related to building scala projects which I personally think are quite significant. Obviously their descriptions are rather shallow, I only tried to capture the most essential aspect of a given project - for more details please check out the linked documentation.


## Purpose
It helped my to structure my knowledge and identify gaps in it, but I hope that others, especially newcomers, could use this cheat sheet as a guide in this, not so small, labyrinth of tools.

## Build tools

1. [sbt](https://www.scala-sbt.org/) - Official scala build tool. It is the most popular, very matured and has comprehensive documentation. 
  There is also a ton of stuff build on top of it (plugins, integrations etc.). Some people find it hard to grasp.
3. [mill](https://github.com/com-lihaoyi/mill) - Build tool initially created by Li Haoyi. Strives to be simpler than sbt.
4. [fury](https://github.com/propensive/fury) - Build tool created by Jon Pretty. Build definition separated from source code. Changes are made in an imperative style.

## Under the hood

1. [BSP](https://build-server-protocol.github.io/) - Builder server protocol made by JetBrains. Code editor needs to be aware of e.g. what the classpath is and so on, in order to run tests or main application. This protocol allows communicating between code editor and a build tool, so the build tools' specific integrations don't have to be build into code editors and repeated for each new editor. 
2. [LSP](https://microsoft.github.io/language-server-protocol/) - Language server protocol made by Microsoft for Visual Studio code. It extracts language/framework specific stuff out from the code editor to make it lighter and also to reuse language support across all code editors which support LSP. This doesn't overlap with BSP - it is used for code navigation, syntax highlighting etc.
3. [zinc](https://github.com/sbt/zinc) - scala incremental compiler. Many build tools which want to be fast need to implement integration layer for it.
4. [bloop](https://scalacenter.github.io/bloop/) - Bloop is a build server that runs in the background of your machine and serves build requests for a specific workspace. It uses BSP to communicate with IDE and various build tools. It implements the integration layer for zinc, so the build tools don't have to. With this in your tool belt the build tool is only responsible for parsing the build definition and fetching dependencies.
5. [metals](https://scalameta.org/metals/) - Language server for scala. Uses LSP to communicate with IDE and BSP to communicate with build tools.
6. [semanticDB](https://scalameta.org/docs/semanticdb/guide.html) - In order to power up the huge set of tools with rich features you need to know more than just a code structure. SemanticDB is a place when compiler puts that information for the latter use of other tools.
7. [coursier](https://github.com/coursier/coursier) - coursier is a dependency resolver. It can be used as a standalone tool or by the build tools to fetch dependencies. Recently, sbt started using it.

## Others

1. [scala-steward](https://github.com/scala-steward-org/scala-steward) - bot to automatically update your dependencies. Similar to github's dependabot but tailored for scala.

## Linters & formatters
1. [scalafmt](https://scalameta.org/scalafmt/) - state of the art formatter for your scala code
2. [scalariform](https://github.com/scala-ide/scalariform) - An alternative to scalafmt although it is unable to break long lines.
3. [scalafix](https://github.com/scalacenter/scalafix) - Linter with an ability to fix/migrate your code. Custom rules can be applied when upgrading libraries to automatically migrate your code. Scala-stweard uses it.
4. [scalastyle](http://www.scalastyle.org/) - Linter and style checker. Nowadays, linter part is mostly suppressed by wartremover and scalac flags. Still can be usefull for style checking.
5. [wartremover](https://www.wartremover.org/) - Great linter, in the process of being replaced by scalafix?

## sbt-plugins
(apart from linters and formatters)
1. [sbt-native-pacakger](https://github.com/sbt/sbt-native-packager) - various ways of packaging your application. Usually used for creation of docker images.
2. [sbt-assembly](https://github.com/sbt/sbt-assembly) - packages your application as a fat jar
3. [sbt-ci-release](https://github.com/olafurpg/sbt-ci-release) - Sbt plugin to automate releases to Sonatype and Maven Central from GitHub Actions or Travis. Version is derived from git tags. Uses: sbt-dynver, sbt-pgp, sbt-sonatype, sbt-git

4. [sbt-release](https://github.com/sbt/sbt-release) - Configure your release process as a series of release steps in scala code. Version dervied from version file. Uses sbt-pgp and sbt-ci-release.
5. [sbt-git](https://github.com/sbt/sbt-git) - calling git from sbt. Used by sbt-ci-release
6. [sbt-tpolecat](https://github.com/DavidGregory084/sbt-tpolecat) - recommended set of compiler flags
7. [sbt-dynver](https://github.com/dwijnand/sbt-dynver) - is an sbt plugin to dynamically set your version from git.
8. [sbt-pgp](https://github.com/sbt/sbt-pgp) - calling pgp binary from sbt
9. [sbt-sonatype](https://github.com/xerial/sbt-sonatype) - A sbt plugin for publishing your project to the Maven central repository through the REST API of Sonatype Nexus.
10. [sbt-pack](https://github.com/xerial/sbt-pack) - Create distributable scala packages togheter with the launch script. An alternative to sbt-assembly.
11. [sbt-travis-ci](https://github.com/dwijnand/sbt-travisci) - sbt-travisci is an sbt plugin to integrate with Travis CI. ?? HOW?
12. [sbt-github-actions](https://github.com/djspiewak/sbt-github-actions) - Can generate github workflow from sbt build.
13. [sbt-updates](https://github.com/rtimush/sbt-updates) - Display your sbt project's dependency updates.

## github actions
1. [coursier-cache-action](https://github.com/coursier/cache-action) - A GitHub action to save / restore the coursier / sbt / mill / Ammonite caches of your build.
2. [setup-scala](https://github.com/olafurpg/setup-scala) - A GitHub Action to install Java via Jabba and sbt.

