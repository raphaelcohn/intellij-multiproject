# intellij-multiproject
[intellij-multiproject] is a MIT-licensed shell script to make it easy to embed other IntelliJ projects that are libraries within a master project. To use it from another project, add it as a submodule in `tools/intellij-multiproject` then `ln -s tools/intellij-multiproject/intellij-multiproject-git-hook git-pull-hook`.

## What is combined
* Modules
* Artifacts (output paths are re-written)
* Library definitions (subprojects overwrite master; last one wins)

## What isn't combined

### What could be
* Copyright profiles are not combined (use a scope to exclude the library code)
  * They could be with some work

### What won't be

* It is not possible to combine the version of Java, or the Java SDKs
  * This can cause problems if there is a difference in the version of Java in the master project and sub-projects
  * It can be overcome by explicitly setting the module's JDK and Java version
* Output path overrides may not work as expected, but it is rare to override a project output path with a per-module one for libraries
* Compiler settings are not combined
* Run configurations are not combined
* Code style settings are not combined (it is recommended to stick to make major edits using sub-projects)
* Inspection Profiles are not combined
