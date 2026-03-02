pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E24C090D28A488B0EBFB57D611E91F35.gr7.ap-south-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
	                sleep 60
                    }
                    
                }
            
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://E24C090D28A488B0EBFB57D611E91F35.gr7.ap-south-2.eks.amazonaws.com']]) {
                sh "kubectl get svc -n webapps"
                    }
                
            }
        }
    }
}
