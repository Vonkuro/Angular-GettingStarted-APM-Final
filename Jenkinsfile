pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                dir ('APM-Final') {
                    sh "${env.npm} install"
                    sh "${env.ng} build"
                }
            }
        }
        stage('Unit test') {
            steps {
                dir ('APM-Final') {
                    sh "${env.npm} test"
                }
            }
        }
        stage('Package') {
            steps {
                sh 'zip -r APM.zip ./APM-Final/dist'
            }
        }
    }
    post {
        success {
            archiveArtifacts artifacts: './APM.zip', fingerprint: true
        }
    }
}