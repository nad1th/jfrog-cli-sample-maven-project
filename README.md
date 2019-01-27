# Build & publish sample maven project using Jfrog CLI via Jenkins

Project use Artifactory to resolve maven dependencies and publish build artifacts. Artifactory repos can be managed via configuration.yml file. To run the project in Jenkins, add credential ID "ARTIFACTORY_CREDENTIALS" under global credentials and provide authentication details for your local artifactory instance. Modify the artifactory url defined in Jenkinsfile if needed.
