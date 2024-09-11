pipeline {
    agent any
    stages {
        
        stage('Build') {
            steps {
                script {
                    sh "docker build -t mohamedmtolba/nginx-app:${BUILD_NUMBER} ."
                    
                   
                      withCredentials([usernamePassword(credentialsId: 'DockerHub', passwordVariable: 'DOCKER_PASS', usernameVariable: 'DOCKER_USER')]) {
                        sh "docker login -u $DOCKER_USER -p $DOCKER_PASS"
                    
                    
                    sh "docker push mohamedmtolba/nginx-app:${BUILD_NUMBER}"
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    echo "Deploying on Kubernetes..."
                    sh "kubectl create namespace k8sname"
                    sh "kubectl -n k8sname apply -f deployment.yml"
                    sh "kubectl -n k8sname apply -f service.yml"
                }
            }
        }
    }
}