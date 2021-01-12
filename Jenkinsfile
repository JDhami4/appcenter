pipeline {
    agent any
    environment {
        APPCENTER_API_TOKEN = credentials('appcenter-api-token')
    }
    tools {nodejs "node"}
    
    stages {
        stage('Test') {
            steps {
                sh 'appcenter apps list'
            }
        }
        stage('Publish') {
            steps {
                appCenter apiToken: APPCENTER_API_TOKEN,
                    ownerName: 'T-Mobile-USA-Inc.',
                    appName: 'BusinessHub-Connect-MacOS',
                    pathToApp: 'emptyfile.dmg',
                    distributionGroups: 'Collaborators',
                    buildVersion: '1.0'
            }
        }
    }
}
