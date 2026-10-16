pipeline {
    agent any

    stages {
        stage('Build Website') {
            steps {
                sh 'docker build -t my-website .'
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                docker rm -f my-website || true
                docker run -d --name my-website \
                  --restart unless-stopped \
                  -p 8081:80 my-website
                '''
            }
        }
    }
}
