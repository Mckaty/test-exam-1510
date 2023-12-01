pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Deploy Demo App') {
            steps {
                sh 'kubectl apply -f /var/lib/jenkins/demo-app/demo-deploy.yaml'
            }
        }
        stage('Get Deploy') {
            steps {
                sh 'kubectl get deploy,pod -n dev-demo-ns'
            }
        }
        stage('Scale POD') {
            steps {
                sh 'kubectl scale deployment -n dev-demo-ns demo-deploy --replicas=2'
            }
        }
        stage('Check Scale POD') {
            steps {
                sh 'kubectl get deploy,pod -n dev-demo-ns'
            }
        }
    }
}

