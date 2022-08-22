pipeline {
    agent any
    environment{
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    }
    stages {
        stage('Checkout') {
            steps {
                sh 'git config --global --unset http.proxy'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/lgordillom/To-Do-App.git']]])
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t lgordillom/to-do-app:latest ./app'            
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'           
            }
        }
        stage('Push') {
            steps {
                sh 'docker push lgordillom/to-do-app:latest'          
            }
        }
    }
}pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {ad           steps {sadas
                echo 'Deploying....'
            }
        }
    }
}