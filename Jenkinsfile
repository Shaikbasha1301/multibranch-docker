pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image3 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image3 basha10/paytmapp1:movie'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: '8b52ef8b-444a-4a1d-91a9-29f73da4beae') {
                        sh 'docker push basha10/paytmapp1:movie'
                    }
                }
            }
        }
        
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movieapp1 -p 1515:80 basha10/paytmapp1:movie'
            }
        }
    }
}
