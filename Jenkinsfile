pipeline {
    agent any

    environment {
        ANSIBLE_PLAYBOOK = '/etc/ansible/deploy_python.yml'
        ANSIBLE_INVENTORY = '/etc/ansible/hosts'
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Checkout your code repository if needed
                // Example:
                // git 'https://github.com/your-repo.git'
                echo 'Checking out code...'
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
                    // Ensure Ansible is installed and available
                    // Run the Ansible playbook
                    ansiblePlaybook(
                        playbook: env.ANSIBLE_PLAYBOOK,
                        inventory: env.ANSIBLE_INVENTORY,
                        extras: '--ask-become-pass' // Use if your playbook requires sudo
                    )
                }
            }
        }
    }

    post {
        always {
            // Optional: Archive artifacts, send notifications, etc.
            echo 'Pipeline finished.'
        }
    }
}
