pipeline {
    agent any

    stages {
        stage('Print Hello World') {
            steps {
                echo 'Hello, World!'
            }
        }

        stage('Execute playbook') {
            steps {
                ansiblePlaybook disableHostKeyChecking: true, installation: 'ansible', inventory: '/etc/ansible/hosts', playbook: 'hello_world.yaml', vaultTmpPath: ''
            }
        }


        // Add more stages and steps as needed
    }

    post {
        success {
            echo 'Jenkins Pipeline executed successfully!'
            // Add post-build actions here if needed
        }

        failure {
            echo 'Jenkins Pipeline failed!'
            // Add post-build actions for failure cases if needed
        }
    }
}