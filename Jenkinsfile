pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                echo "Cloning GitHub repository..."
                git branch: 'main',
                    url: 'https://github.com/yogeshsunny05/iac-fcs-pipeline.git',
                    credentialsId: 'github-creds'
            }
        }

        stage('Run IaC Scan Test') {
            steps {
                echo "Running IaC scan..."
                bat '"C:\\FalconCLI\\fcs.exe" scan iac --path . --upload'
            }
        }
    }

    post {
        always {
            echo "Pipeline execution finished."
        }
        success {
            echo "IaC scan completed successfully and results uploaded to FCS."
        }
        failure {
            echo "IaC scan failed. Check logs for errors."
        }
    }
}
