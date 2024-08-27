pipeline {
    agent any

    environment {
        ANSIBLE_PLAYBOOK = '/etc/ansible/deploy_python.yml'
        ANSIBLE_INVENTORY = '/etc/ansible/hosts'
        SSH_PRIVATE_KEY = '/path/to/private/key'  // Update this if using a specific SSH key
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code...'
                // Add SCM checkout steps if needed
            }
        }

        stage('Verify SSH Key') {
            steps {
                script {
                    // Check if the SSH key is accessible
                    sh 'ls -l ${SSH_PRIVATE_KEY}'
                    sh 'cat ${SSH_PRIVATE_KEY}'
                }
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
                    ansiblePlaybook(
                        playbook: env.ANSIBLE_PLAYBOOK,
                        inventory: env.ANSIBLE_INVENTORY,
                        extraVars: [ansible_ssh_private_key_file: env.SSH_PRIVATE_KEY]
                    )
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
