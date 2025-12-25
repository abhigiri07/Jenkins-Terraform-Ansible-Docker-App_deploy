pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'https://github.com/abhigiri07/devops-cicd-project.git'
            }
        }

        stage('Terraform Apply') {
            steps {
                dir('terraform') {
                    sh '''
                    terraform init
                    terraform apply -auto-approve
                    '''
                }
            }
        }

        stage('Configure EC2') {
            steps {
                dir('ansible') {
                    sh '''
                    ansible-playbook -i inventory.ini docker-install.yml
                    ansible-playbook -i inventory.ini deploy-app.yml
                    '''
                }
            }
        }
    }
}
