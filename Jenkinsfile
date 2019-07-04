pipeline {
    agent any 
    tools {
        maven 'apache-maven-3.6.1'
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
