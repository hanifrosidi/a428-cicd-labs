pipeline {
    agent {
        docker {
            image "node:16-buster-slim"
            args "-p 4000:4000"
        }
    }
    triggers {
        pollSCM('H/2 * * * *')
    }
    stages {
        stage("Build") {
            steps {
                sh "npm install"
            }
        }
        stage("Test") {
            steps {
                sh "./jenkins/scripts/test.sh"
            }
        }
        stage("Test") {
            steps {
                sh('./jenkins/scripts/test.sh')
            }
        }
    }
}