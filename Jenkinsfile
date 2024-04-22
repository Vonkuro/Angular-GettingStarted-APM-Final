pipeline {
    stages {
        stage('Build') {
            steps {
                dir ('APM-Final') {
                    sh 'npm install'
                    sh 'ng build'
                }
            }
        }
        stage('Unit test') {
            steps {
                dir ('APM-Final') {
                    sh 'npm test'
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