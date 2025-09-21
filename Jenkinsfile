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
                sh 'docker tag image3 vamshisuraj/phonepay:movie'
            }
        }
        stage ("Push") {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker') {
                    sh 'docker push vamshisuraj/phonepay:movie'
                        
                    }
                }
            }
        }
        stage ("Deploy") {
            steps {
                sh 'docker run -itd --name movie-app -p 8888:80 vamshisuraj/phonepay:movie'
            }
        }
    }
}
