pipeline {
    agent any
    tools {
        terraform 'Terraform'
    }
    environment {
        class_name = "iitc"
    }

    stages {
        stage('Git PUll SCM') {
            steps {
                    git branch: 'main', credentialsId: 'SSh-github', url: 'git@github.com:AmitShemeshCrowd/AmitTFDemo-conf.git'
            }
        }
        stage('terraform version') {
            steps {
                sh 'terraform --version'
            }
        }
        
        stage('call variables') {
            steps {
                sh 'echo $JOB_NAME'
                sh 'echo ${class_name}'
            }
        }
        
        stage('terraform init') {
            steps {
                sh 'terraform init'
            }
        }
        // 
        
        stage('terraform plan') {
            steps {
                sh 'terraform plan'
            }
        }
        
        stage('terraform apply') {
            steps {
                sh 'terraform destroy -auto-approve'
            }
        }
        
        // stage('CleanWS') {
        //     steps {
        //         cleanWs()
        //     }
        // }
    }
}

