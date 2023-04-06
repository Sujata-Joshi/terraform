pipeline{
    agent any
    
    stages{
        stage('Azure'){
            steps{
                sh 'az cloud set --name AzureUSGovernment'   
            }
        }
        stage('Azure1'){
            steps{
                sh 'az account set --subscription="56bd9e98-6237-4a3c-9aa8-f13046e1f606"'   
            }
        }
        stage('Azure2'){
            steps{
                sh 'az ad sp create-for-rbac --role="Contributor" --scopes="/subscriptions/56bd9e98-6237-4a3c-9aa8-f13046e1f606"'
            }
        }
        stage('Azure3'){
            steps{
                sh 'az login --service-principal -u CLIENT_ID -p CLIENT_SECRET --tenant TENANT_ID'
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