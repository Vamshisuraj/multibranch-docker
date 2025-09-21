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
                sh 'docker tag image2 vamshisuraj/phonepay:bus'
            }
        }
        stage ("Push") {
            steps {
                script {
                   withDockerRegistry(credentialsId: 'docker') {
                    sh 'docker push vamshisuraj/phonepay:bus'
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name bus-app -p 7777:80 vamshisuraj/phonepay:bus'
            }
        }
    }
}
