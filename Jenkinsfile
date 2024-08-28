pipeline {
    agent any

    environment {
        ANSIBLE_PLAYBOOK = '/etc/ansible/deploy_python.yml'
        ANSIBLE_INVENTORY = '/etc/ansible/hosts'
        SSH_PRIVATE_KEY = '/var/lib/jenkins/.ssh/id_rsa'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code...'
                // Add SCM checkout steps if needed
            }
        }

       

        stage('Run Ansible Playbook') {
            steps {
                script {
                    sh '''
                        echo "Running Ansible Playbook"
                        ansible-playbook  ${ANSIBLE_PLAYBOOK} -i ${ANSIBLE_INVENTORY} --private-key=${SSH_PRIVATE_KEY}
                    '''
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
