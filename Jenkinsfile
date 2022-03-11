pipeline {
    agent any
    stages {
        stage ('(1) Git clone') {
            steps {
                git branch: 'main', url: 'https://github.com/shay79il/Trigo-infra'
            }
        }
        stage ('(2) Deploy apps-ingress.yml') {
            steps {
                sh 'kubectl apply -f apps-ingress.yml'
            }
        }
    }
}