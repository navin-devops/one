pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Terraform Init') {
            steps {
                sh 'terraform init'
            }
        }

        stage('Terraform Plan') {
            steps {
                sh 'terraform plan -out=tfplan'
            }
        }

        stage('Terraform Apply') {
            steps {
                input message: 'Approve Terraform Apply?', ok: 'Apply'
                sh 'terraform apply -auto-approve tfplan'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
