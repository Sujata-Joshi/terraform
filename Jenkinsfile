pipeline{
    agent any
    environment {
        MY_CRED = credentials('AzureTerraform')
    }
    stages{
        stage('build') {
            steps {
                sh 'az login --service-principal -u $MY_CRED_CLIENT_ID -p $MY_CRED_CLIENT_SECRET -t $MY_CRED_TENANT_ID'
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