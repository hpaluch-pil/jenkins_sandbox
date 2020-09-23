# jenkins_sandbox

## Introduction

Sample generated Jenkins plugin (from Archetype) to test Jenkins behaviour

Will be used to debug random issues, for example:
- https://issues.jenkins-ci.org/browse/JENKINS-63737

= Setup - Eclipse

- Import... -> Import Existing Maven Project
- Run -> Debug Configurations -> Maven Build -> New
  - Name:  `jenkins_sandbox hpi_run`
  - Base directory: `${workspace_loc:/jenkins_sandbox}`
  - Goals: `hpi:run`
- right-click project -> Maven -> Download Sources
- Navigate -> Open Type -> LDAP Search Builder
  - put breakpoint at `search()`  
  