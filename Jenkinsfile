pipeline {
    agent {
        label "yomna"
    }
    stages {
        stage('Build') {
            steps {
                sh "docker build . -t gcr.io/sincere-hearth-377212/grad-app"
                sh "docker push gcr.io/sincere-hearth-377212/grad-app"
            }
        }
        stage('Deploy') {
            steps {
                sh "kubectl apply -f kubernetes/app-py.yaml"
                sh "kubectl apply -f kubernetes/app-lb.yaml"
            }
        }
    }
}