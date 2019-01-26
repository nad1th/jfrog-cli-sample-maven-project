node {
    stage ('GIT Clone') {
        checkout scm
    }
    stage ('Config CLI Artifactory') {
        sh "jfrog rt c $ARTIFACTORY_ID --url=$ARTIFACTORY_URL --user=$ARTIFACTORY_USER --password=$ARTIFACTORY_PASSWORD"
    }
    stage ('Maven Build' ) {
        sh "jfrog rt mvn 'clean install' configuration.yml --build-name=${env.JOB_NAME} --build-number=${env.BUILD_NUMBER}"
    }
    stage ('Unit Test') {
        sh "jfrog rt mvn test configuration.yml"
    }
    stage ('Get GIT info'){
        sh "jfrog rt bag ${env.JOB_NAME} ${env.BUILD_NUMBER}"
    }
    stage ('Collect Build Env'){
        sh "jfrog rt bce ${env.JOB_NAME} ${env.BUILD_NUMBER}"
    }
    stage ('Publish Build'){
        sh "jfrog rt bp ${env.JOB_NAME} ${env.BUILD_NUMBER}"
    }
}
