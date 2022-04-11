pipeline {
    agent any

    environment{
        GIT_TOKEN='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'
    }

    stages {
        stage('Checkout') {
            steps {
                cleanWs()
                checkout scm
                sh 'git fetch --all --tags'
            }
        }
        stage('Initialization') {
            steps {
                sh 'FUTURE_VERSION=$(jx-release-version)'
                withCredentials([gitUsernamePassword(credentialsId: '898e10c6-e0fa-453a-9e40-8ecf3c80be63', gitToolName: 'Default')]) {
                    sh 'git config user.name moskalov'
                    sh 'git config user.email jenkins@jenkins.com'
                    sh 'jx-release-version -tag'
                }
            }
        }
    }
}
