pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'serverUrl: 'https://1CB3A34CAE28FCD03899DAB029541312.gr7.us-east-1.eks.amazonaws.com'']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'serverUrl: 'https://1CB3A34CAE28FCD03899DAB029541312.gr7.us-east-1.eks.amazonaws.com'']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
