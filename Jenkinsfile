pipeline {
    agent any

    stages {
        stage('Verify FCS CLI') {
            steps {
                echo "Testing FCS CLI connectivity..."
                bat '"C:\\FalconCLI\\fcs.exe" health-check'
            }
        }
    }
}
