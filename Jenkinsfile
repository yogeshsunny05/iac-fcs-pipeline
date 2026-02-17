pipeline {
    agent any

    environment {
        FCS_CLIENT_ID     = credentials('fcs-client-id')
        FCS_CLIENT_SECRET = credentials('fcs-client-secret')
        FALCON_API_URL    = 'https://api.us-2.crowdstrike.com'
    }

    stages {
        stage('Checkout Code') {
            steps {
                echo "Cloning GitHub repository..."
                git branch: 'main',
                    url: 'https://github.com/yogeshsunny05/iac-fcs-pipeline.git',
                    credentialsId: 'github-creds'
            }
        }

        stage('Run IaC Scan') {
            steps {
                echo "Running IaC scan using environment variables..."
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
