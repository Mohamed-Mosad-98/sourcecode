pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'Master', url: 'https://github.com/Mohamed-Mosad-98/sourcecode.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t nodeapp:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f nodeapp || true
                docker run -d --name nodeapp -p 3000:3000 nodeapp:latest
                '''
            }
        }
    }
}
