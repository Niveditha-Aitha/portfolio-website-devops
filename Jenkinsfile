pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Niveditha-Aitha/portfolio-website-devops.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t portfolio-site:v1 .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker rm -f portfolio || true

                docker run -d \
                --name portfolio \
                -p 8080:80 \
                portfolio-site:v1
                '''
            }
        }
    }
}
