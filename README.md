# jenkins_sandbox

## Introduction

Sample generated Jenkins plugin (from Archetype) to test Jenkins behaviour

Will be used to debug random issues, for example:
- https://issues.jenkins-ci.org/browse/JENKINS-63737

# Setup - Eclipse

- Import... -> Import Existing Maven Project
- Run -> Debug Configurations -> Maven Build -> New
  - Name:  `jenkins_sandbox hpi_run`
  - Base directory: `${workspace_loc:/jenkins_sandbox}`
  - Goals: `hpi:run`
- right-click project -> Maven -> Download Sources
- Navigate -> Open Type -> enter: `LDAPSearchBuilder` 
  - only one class should be found
  - open that class and
  - put breakpoint at `search()`  
  

## Resolving AD plugin sources for Debug  
  
I had no luck, so I did it manually.
* from CLI run:

```
mvn dependency:sources
```

* then do this:
  - Run -> Debug Configurations ...
  - select our `jenkins_sandbox hpi_run`
  - click on "Source" tab
  - Add External Archive
  - Browse... and select manually path like:

```
YOUR_HOME\.m2\repository\org\jenkins-ci\plugins\active-directory\2.18\active-directory-2.18-sources.jar 
```
  
- Put breakpoint on interesting method, for example:

```
hudson.plugins.active_directory.LDAPSearchBuilder.search()
```

- then Debug `jenkins_sandbox hpi_run`
- 1st login to Jenkins (via Web UI or call some API)
- breakpoint should be reached with full source.

  
