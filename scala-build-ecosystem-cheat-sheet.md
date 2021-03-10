# Scala build ecosystem cheet sheet


## Build tools

1. [sbt](https://www.scala-sbt.org/) - Official scala build tool. It is the most popular, very matured and has comperhensive documentation. 
  There is also a ton of stuff build on top of it (plugins, integrations etc.). Some people find it hard to grasp.
3. [mill](https://github.com/com-lihaoyi/mill) - Build tool initially created by Li Haoyi. Strives to be simpler than sbt.
4. [furry](https://github.com/propensive/fury) - Build tool created by Jon Pretty. Build definition separated from source code. Imperative approach to edition and maintenance.

## IDE

1. Intelij IDEA
2. VS code + metals -> 
3. Ensime - ???

## Under the hood

1. [BSP](https://build-server-protocol.github.io/) - Builder server protocol made by JetBrains. Code editor needs to be aware of e.g. what the classpath is and so on, in order to run tests or main application. This protocol allows to comunicate between code editor and a build tool, so the build tools' specific integrations don't have to be build into code editors and repeated for each new editor. 
2. [LSP](https://microsoft.github.io/language-server-protocol/) - Language server protocol made by Microsoft for Visual Studio code. It extracts language/framework specific stuff out from the code editor to make it ligher and also to reuse language support acros all code editors which support LSP. This doesn't overlap with BSP - it is used for code navigation, syntax highlithing etc.
3. [zinc](https://github.com/sbt/zinc) - scala incremental compiler. Many build tools which want to be fast need to implement integration layer for it.
4. [bloop](https://scalacenter.github.io/bloop/) - Bloop is a build server that runs in the backgroud of your machine and serves build requests for a specific workspace. It uses BSP to communicate with IDE and various build tools. It implements the integration layer for zinc, so the build tools don't have to. With this in your toolbelt the build tool is only responsible for parsing the build definition and fetching dependencies.
5. metals
6. semanticDB
7. [coursier](https://github.com/coursier/coursier) - coursier is a dependency resolver. It can be used as a standalone tool or by the build tools to fetch dependencies. Recently, sbt started using it.

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
3. sbt-ci-release
4. sbt-release
5. sbt-git - calling git from sbt. Used by sbt-ci-release
6. [sbt-tpolecat](https://github.com/DavidGregory084/sbt-tpolecat) - recommended set of compiler flags
7. sbt-dynver
8. sbt-pgp - calling pgp binary from sbt
9. sbt-travis-ci
10. sbt-github-actions

## github actions
1. [coursier-cache-action](https://github.com/coursier/cache-action) - A GitHub action to save / restore the coursier / sbt / mill / Ammonite caches of your build.

