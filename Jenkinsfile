pipeline {
    agent any

    environment {
      AWS_ACCESS_KEY_ID = credentials('AWS_ACCESS_KEY_ID')
      AWS_SECRET_ACCESS_KEY = credentials('AWS_SECRET_ACCESS_KEY')
    }

    tools {
        terraform 't3'
    }
    stages {
        stage('Git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/SanyaRokin/finalexam.git'
            }
        }
        stage("Terraform init") {
            steps {
                sh 'terraform init'
            }
        }
        stage("Terraform apply") {
            steps {
                sh 'terraform plan'
                sh 'terraform apply --auto-approve'
            }
        }
        stage ('Install Ansible aws modules') {
            steps {
                sh "ansible-galaxy collection install community.aws"
                sh "ansible-galaxy collection install community.general"
            }
       }
       stage ('Start ansible playbook') {
            steps {
                ansiblePlaybook become: true, colorized: true, credentialsId: 'sshaws', disableHostKeyChecking: true, installation: 'ansible', playbook: 'ansible.yml'
            }
       }

    }
}
