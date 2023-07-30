pipeline {
    agent any
    stages {
        stage('Pull Code From GitHub') {
            steps {
                git 'https://github.com/VINAYAGAM1/K8S.git'
            }
        }
        stage('BUILDER VINAYAK') {
            steps {
                sh 'sudo docker build -t jass /var/lib/jenkins/workspace/kuber'
                sh 'sudo docker tag jass vinayagamvaratha/jass:latest'
                sh 'sudo docker tag jass vinayagamvaratha/jass:${BUILD_NUMBER}'
            }
        }
        stage('PUSH DOC6 VINAYAK') {
            steps {
                sh 'sudo docker image push vinayagamvaratha/jass:latest'
                sh 'sudo docker image push vinayagamvaratha/jass:${BUILD_NUMBER}'
            }
        }
        stage('vinayak DEPLOY k8s') {
            steps {
                sh 'sudo kubectl apply -f /var/lib/jenkins/workspace/kuber/pod.yaml'
                sh 'sudo kubectl rollout restart deployment loadbalancer-pod'
            }
        }
    }
}
