pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t myapp .'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Running Docker container...'
                sh 'docker run -d -p 8081:80 myapp'
            }
        }
    }
}
