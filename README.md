# Build & publish sample maven project using Jfrog CLI via Jenkins

Project use Artifactory to resolve maven dependencies and publish build artifacts. Artifactory repos can be managed via configuration.yml file. To run the project in Jenkins use parameterized build option in Jenkins pipeline and add below parameters.
  1. ARTIFACTORY_ID
  2. ARTIFACTORY_URL
  3. ARTIFACTORY_USER
  4. ARTIFACTORY_PASSWORD
