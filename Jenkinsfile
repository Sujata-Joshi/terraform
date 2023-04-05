pipeline{
    agent any
    
    stages{
        stage('GitCode'){
             steps{
                git url : 'https://github.com/Sujata-Joshi/terraformJenkinsApril2023.git',
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