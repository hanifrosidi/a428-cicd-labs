pipeline {
    agent {
        docker {
            image "node:16-buster-slim"
            args "--network host"
        }
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
        stage("Deploy") {
            steps {
                sh "./jenkins/scripts/deliver.sh"

                input message: "Sudah selesai menggunakan React App? (Klik \"Proceed\" untuk mengakhiri)"

                echo "Application is running for 1 minute..."
                sleep(time: 1, unit: 'MINUTES')
                
                sh "./jenkins/scripts/kill.sh"

            }
        }
    }
}