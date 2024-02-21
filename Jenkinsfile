pipeline {
    agent any

    stages {
        stage('Cloning Git Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/andrebrkk/jk-publick-gh.git'
            }
        }
        stage('Building image') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Deploying Application') {
            steps {
                sh '''
                cd /opt/docker/app
                docker compose up -d
                '''
            }
        }
        stage('Maintence application') {
            steps {
                sh 'docker compose down'
            }
        }
    }
}
