node {
    stage('Build') {
        def myImage = docker.build("lgordillom/to-do-app:latest")
        docker.withRegistry('', 'DockerHub') {
            myImage.push("latest")
        }
    }
    
    node {
        stage('Unit Tests') {
            echo "Unit Tests"
        }
        stage('System Tests') {
            echo "System Tests"
        }
    }

    stage('Deploy') {
        echo 'deploying'
        steps {
                sh 'ssh vagrant@10.0.0.11 "docker stop todo;docker pull lgordillom/to-do-app:latest;docker run -d -p 3000:3000 --name to-do-app lgordillom/to-do-app:latest" '
            }
    }
}