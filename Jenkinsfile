pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                // Clone your GitHub repository
                git branch: 'main',
                    url: 'https://github.com/yogeshsunny05/iac-fcs-pipeline.git',
                    credentialsId: 'github-creds'
            }
        }

        stage('Run IaC Scan') {
            steps {
                // Run FCS IaC scan using the CLI already configured on this machine
                bat 'fcs scan iac --path . --upload'
            }
        }
    }

    post {
        always {
            echo "IaC scan completed."
        }
        success {
            echo "Scan successful, results uploaded to FCS."
        }
        failure {
            echo "Scan failed. Check logs for errors."
        }
    }
}
