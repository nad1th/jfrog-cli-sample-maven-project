node {
    def ARTIFACTORY_ID = 'artifactory'
    def ARTIFACTORY_URL = 'http://localhost:8081/artifactory'

    stage ('GIT Clone') {
        checkout scm
    }
    stage ('Config CLI Artifactory') {
        sh "curl -fL https://getcli.jfrog.io | sh"
        withCredentials([usernamePassword(credentialsId: 'ARTIFACTORY_CREDENTIALS', passwordVariable: 'ARTIFACTORY_PASSWORD', usernameVariable: 'ARTIFACTORY_USER')]) {
            sh "./jfrog rt c $ARTIFACTORY_ID --url=$ARTIFACTORY_URL --user=$ARTIFACTORY_USER --password=$ARTIFACTORY_PASSWORD"
        }
    }
    stage ('Maven Build & Publish' ) {
        sh "./jfrog rt mvn 'clean install -DskipTests=true' configuration.yml --build-name=${env.JOB_NAME} --build-number=${env.BUILD_NUMBER}"
    }
    stage ('Unit Test') {
        sh "./jfrog rt mvn test configuration.yml"
    }
    stage ('Get GIT info'){
        sh "./jfrog rt build-add-git ${env.JOB_NAME} ${env.BUILD_NUMBER}"
    }
    stage ('Collect Build Env info'){
        sh "./jfrog rt build-collect-env ${env.JOB_NAME} ${env.BUILD_NUMBER}"
    }
    stage ('Publish Build Info'){
        sh "./jfrog rt build-publish ${env.JOB_NAME} ${env.BUILD_NUMBER}"
        cleanWs()
    }
}
