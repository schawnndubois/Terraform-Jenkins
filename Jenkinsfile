pipeline {

    parameters {
        booleanParam(name: 'autoApprove', defaultValue: false, description: 'Automatically run apply after generating plan?')
    } 
    environment {
        AWS_ACCESS_KEY_ID     = credentials('AWS_ACCESS_KEY_ID')
        AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }

   agent  any
    stages {
        stage('checkout') {
            steps {
                 script{
                        dir("terraform")
                        {
                            git "https://github.com/schawnndubois/Terraform-Jenkins.git"
                        }
                    }
                }
            }

  stage('Plan') {
            steps {
                sh 'pwd;cd terraform/ ; terraform init'
                sh " terraform plan -out tfplan"
            }
        }
    }

  }
