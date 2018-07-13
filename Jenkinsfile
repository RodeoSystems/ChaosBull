pipeline { 
    agent any 
    stages {
        stage('Build'){
            steps {
                sh 'echo "Compiling..."'
                sh 'echo "Building for Embedded Target 1"'
            }
        }
        stage('Test'){
            steps {
                sh 'echo "Unit testing compiled libraries..."'
                awsCodeBuild projectName: 'jenkins_generic', credentialsType: 'keys', region: 'us-east-2', sourceControlType: 'jenkins', envVariables: '[{TEST,veldboom}]'
            }
        }
        stage('Preflight'){
            steps {
                sh 'echo "Running external test battery from QA"'
            }
        }
        stage('Deployment'){
            steps {
                sh 'echo "Releasing to customers"'
            }
        }
    }
}