pipeline{
    agent any
    
    stages{
        stage('Azure')
        {
            steps{
               withCredentials([azureServicePrincipal(clientIdVariable: 'd0e8d40e-647d-4920-9f6b-be9c5416daeb', clientSecretVariable: '4ca501cf-1dd3-4183-b143-0d49ec66d1e7', credentialsId: 'AzureTerraform', subscriptionIdVariable: '56bd9e98-6237-4a3c-9aa8-f13046e1f606', tenantIdVariable: '628f5730-e1f2-40fd-be68-41a34ad5ecdc')]) {
                    sh 'az login --service-principal -u $clientIdVariable -p $clientSecretVariabl -t $tenantIdVariable'
                }
            }
        }
        stage('GitCode'){
            steps{
                git url : 'https://github.com/Sujata-Joshi/terraform.git',
                branch : 'master'
            }
        }
        stage('Terraform initialization') {
            steps{
                sh 'terraform init'
            }
        }
        stage('Terraform format') {
            steps{
                sh 'terraform fmt'
            }
        }    
        stage('Terraform validation') {
            steps{
                sh 'terraform validate'
            }
        }
        stage('Terraform Apply') {
            steps{
                sh 'terraform apply -auto-approve'
            }
        }
    }
}