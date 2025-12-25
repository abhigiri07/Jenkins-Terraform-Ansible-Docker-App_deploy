pipeline {
    agent { label 'ansible' }

    environment {
        ANSIBLE_HOST_KEY_CHECKING = 'False'
    }

    stages {

        stage('Clone Repo') {
            steps {
                git 'https://github.com/abhigiri07/devops-cicd-project.git'
            }
        }


        stage('Configure Target EC2') {
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
