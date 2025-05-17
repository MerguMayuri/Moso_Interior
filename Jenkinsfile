pipeline {
    agent any
    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/YOUR_USERNAME/moso-interior-site.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t moso-site .'
            }
        }
        stage('Stop Old') {
            steps {
                sh '''
                docker stop moso-container || true
                docker rm moso-container || true
                '''
            }
        }
        stage('Run New') {
            steps {
                sh 'docker run -d --name moso-container -p 80:80 moso-site'
            }
        }
    }
}
