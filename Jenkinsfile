pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                script {
                    def dockerImage = docker.build("Abhishek1296/website-prt-org")
                }
            }
        }
        stage('Deploy') {
            steps {
                withKubeConfig([credentialsId: 'kubeconfig', serverUrl: 'https://k8s-master-ip:6443']) {
                    sh 'kubectl apply -f k8s-deployment.yml'
                }
            }
        }
    }
}
