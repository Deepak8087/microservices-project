pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-deepak', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://CAFE050566965CBFA256148CD637707F.yl4.us-west-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-deepak', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://CAFE050566965CBFA256148CD637707F.yl4.us-west-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
