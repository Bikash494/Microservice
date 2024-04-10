pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5A995F87BFF6D4E6791869D77BFB30C4.gr7.ap-south-1.eks.amazonaws.com']]) {
                // some block
                sh "kubectl apply -f  deployment-service.yml"
                sleep 60
                }
            }
        }
        
        stage ('verify deployment') {
           steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5A995F87BFF6D4E6791869D77BFB30C4.gr7.ap-south-1.eks.amazonaws.com']]) {
                        // some block
                    sh "kubectl get all -n webapps"
                }
            } 
        }
        
    }
}
