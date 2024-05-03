pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F43D8FAFFA4F8AB7DCDA6683317A532C.gr7.eu-west-2.eks.amazonaws.com']]) {
                  sh "kubectl apply -f deployment-service.yml"
                  sleep 60
               } 
            }
        }
    
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'eks', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://F43D8FAFFA4F8AB7DCDA6683317A532C.gr7.eu-west-2.eks.amazonaws.com']]) {
                  sh "kubectl get all -n webapps"
              }
            }
        }    
    }
}
