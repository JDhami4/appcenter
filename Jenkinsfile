pipeline {
    agent any
    
    tools {nodejs "node"}
    
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
        stage('Publish') {
            environment {
                APPCENTER_API_TOKEN = credentials('cf9c28894bac2849aa78ed47e71198fc95799d30')
            }
            steps {
                appCenter apiToken: APPCENTER_API_TOKEN,
                    ownerName: 'T-Mobile-USA-Inc.',
                    appName: 'BusinessHub-Connect-MacOS',
                    pathToApp: 'emptyfile.dmg',
                    distributionGroups: 'Collaborators',
                    buildVersion: '1.0',
                    buildNumber: '1.0.1'
            }
        }
    }
}
