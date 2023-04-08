pipeline{
    agent any
    
    stages{
        stage('Checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/abhishek-bakare/TF-project']])
            }
        }

        stage('tf-init'){
            steps{
                sh 'terraform init -reconfigure'
            }
        }

        stage('tf plan'){
            steps{
                sh 'terraform plan -out=tfplan' 
            }
        }

        stage('tf action'){
            steps{
                echo "Terraform action is ---> ${action}"
                sh 'terraform ${action} "tfplan" --auto-approve'
            }
        }

        }
    }
