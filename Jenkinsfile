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
                sh 'docker tag image1 vamshisuraj/phonepay:bank'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                    sh 'docker push vamshisuraj/phonepay:bank'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bank-app -p 9999:80 vamshisuraj/phonepay:bank'
            }
        }
    }
}
