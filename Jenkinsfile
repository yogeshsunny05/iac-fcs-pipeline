pipeline {
    agent any
    stages {
        stage('Test FCS CLI') {
            steps {
                bat 'fcs health-check'
            }
        }
    }
}
