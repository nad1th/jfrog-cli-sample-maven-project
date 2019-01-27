# jfrog-cli-sample-maven-project

## Build & publish sample maven project to Artifactory using Jfrog CLI via Jenkins

`To make this integration work you will need to have running instance of Jenkins and Artifactory.`

### How to Install Artifactory & Jenkins
Refer [Artifactory Installation guide](https://www.jfrog.com/confluence/display/RTF/Installing+on+Linux+Solaris+or+Mac+OS) & [Jenkins Installation guide](https://jenkins.io/doc/book/installing)

### Setup Artifactory Maven Repositories
Check how to [setup maven repositories](https://jfrog.com/screencast/setting-maven-repository-jfrog-artifactory-less-one-minute/)

### Build Configuration File
To resolve maven dependencies via Artifactory and publish build artifacts to Artifactory, resolver and deployer repos have be defined in [configuration.yml](configuration.yml) file.

### Setup Jenkins pipeline
- Create pipeline job in Jenkins (New Item > Pipeline)
- In the project configuration, select "pipeline script from SCM" and fill out the necessary details. 
- Add credential ID "ARTIFACTORY_CREDENTIALS" under global credentials and provide authentication details for your local artifactory instance

### What is Jfrog CLI
For more information on using Jfrog CLI, refer to the [documentation](https://www.jfrog.com/confluence/display/CLI/CLI+for+JFrog+Artifactory).
