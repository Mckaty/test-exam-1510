pipeline {
    agent {
      label 'jenkins-ubuntu-slave-uat-01'
    }

    stages {
        stage('Check Jenkins Slave UAT') {
            steps {
                echo 'Hello Jenkins Slave UAT 01'
                sh 'hostname'
                sh 'ls -tlr'
                sh 'pwd'
                sh 'date'
            }
        }
        stage('Deploy Demo App') {
            steps {
                sh 'kubectl apply -f demo-deploy.yaml'
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
                sh 'kubectl get all -n dev-demo-ns'
            }
        }
    }
}

