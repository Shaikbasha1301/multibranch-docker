pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image1 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image1 basha10/paytmapp1:bank'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: '8b52ef8b-444a-4a1d-91a9-29f73da4beae') {
                        sh 'docker push basha10/paytmapp1:bank'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bankapp1 -p 1313:80 basha10/paytmapp1:bank'
            }
        }
    }
}
