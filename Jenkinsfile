pipeline {
    agent any

    environment {
        AWS_REGION = 'ap-southeast-1' // Change to your AWS region
        CLUSTER_NAME = 'ticker-eks-cluster' // Change to your EKS cluster name
    }

    stages {
        stage('Deploy to EKS') {
            steps {
                script {
                    sh """
                        aws eks update-kubeconfig --name ${CLUSTER_NAME} --region ${AWS_REGION}
                        kubectl apply -f deploy.yaml
                        kubectl apply -f service.yaml
                    """
                }
            }
        }
    }
}
