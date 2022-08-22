pipeline {
    agent any
    stages {
        stage('Deploy') {
            steps {
                sh 'ssh vagrant@10.0.0.11 "docker stop to-do-app;docker rm to-do-app;docker pull lgordillom/to-do-app:latest;docker run -d -p 3000:3000 --name to-do-app lgordillom/to-do-app" '
            }
        }
    }
}