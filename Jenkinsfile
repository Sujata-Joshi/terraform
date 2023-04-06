pipeline{
    agent any
    
    stages{
        stage('Azure')
        {
            steps{
                withCredentials([azureServicePrincipal('AzureTerraform')]) {
                    sh 'az login --service-principal -u $CLIENT_ID -p $CLIENT_SECRET -t $TENANT_ID'
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