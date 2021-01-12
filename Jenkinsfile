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
                APPCENTER_API_TOKEN = credentials('appcenter-api-token')
            }
            steps {
                appCenter apiToken: APPCENTER_API_TOKEN,
                    ownerName: 'T-Mobile-USA-Inc.',
                    appName: 'BusinessHub-Connect-MacOS',
                    pathToApp: 'emptyfile.dmg',
                    distributionGroups: 'BHC-Devs',
                    buildVersion: '1.0'
            }
        }
    }
}
