pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t my-web-app .'
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d --name my-web-app -p 80:80 my-web-app'
            }
        }
    }
}

