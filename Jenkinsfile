pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t image2 .'
            }
        }
        stage ("Tag") {
            steps {
                sh 'docker tag image2 basha10/paytmapp:bus'
            }
        }
        stage('Push') {
            steps {
                script {
                    withDockerRegistry(credentialsId: '8b52ef8b-444a-4a1d-91a9-29f73da4beae') {
                        sh 'docker push basha10/paytmapp:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 2222:80 basha10/paytmapp:bus'
            }
        }
    }
}
