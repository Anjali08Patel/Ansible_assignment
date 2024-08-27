pipeline {
    agent any

    environment {
        ANSIBLE_PLAYBOOK = '/etc/ansible/deploy_python.yml'
        ANSIBLE_INVENTORY = '/etc/ansible/hosts'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo 'Checking out code...'
                // Add any SCM checkout steps if needed
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
                    ansiblePlaybook(
                        playbook: env.ANSIBLE_PLAYBOOK,
                        inventory: env.ANSIBLE_INVENTORY
                        // Note: Remove `extras` if not needed
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
