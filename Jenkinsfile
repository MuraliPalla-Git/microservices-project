pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'ekscluster-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B91C981BCAF26B4ACD20BBE5289BE43D.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'ekscluster-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://B91C981BCAF26B4ACD20BBE5289BE43D.gr7.eu-north-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
