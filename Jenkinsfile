pipeline {
    agent any
    environment {
        APPCENTER_API_TOKEN = credentials('appcenter-api-token')
    }
    tools {nodejs "node"}
    
    stages {
        stage('Test') {
            steps {
                sh 'appcenter apps list --token $APPCENTER_API_TOKEN'
            }
        }
        stage('Publish') {
            steps {
                sh 'appcenter distribute release -f emptyfile.dmg --build-number 1.0.1 --build-version 3.0 --group Collaborators --token $APPCENTER_API_TOKEN'
            }
        }
    }
}
