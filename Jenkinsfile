pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
        stage('Build') {
            steps {
                sh 'mvn --version'
                sh 'mvn clean install -e'
                nexusPolicyEvaluation advancedProperties: '', failBuildOnNetworkError: false, iqApplication: selectedApplication('testapp01'), iqScanPatterns: [[scanPattern: '**/*.jar'], [scanPattern: '**/*.war'], [scanPattern: '**/*.ear']], iqStage: 'build', jobCredentialsId: 'nexus-iq-server'
            }
        }
    }
}
