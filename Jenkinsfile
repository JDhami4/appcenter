pipeline {
    agent any
    environment {
        APPCENTER_API_TOKEN = credentials('appcenter-api-token')
    }
    tools {nodejs "node"}
    
    stages {
        stage('Publish Mac') {
            input {
                message 'Input Parameters?'
                ok 'Done!'
                parameters {
                    string(name: 'PATH_TO_BUILD', defaultValue: '', description: 'Path to the dmg file, relative to the root of the repo')
                    choice(name: 'APP_NAME', choices: ["T-Mobile-USA-Inc./BusinessHub-Connect-MacOS","T-Mobile-USA-Inc./BusinessHub-Connect-Win"], description: 'The name of the application (in app-center)')
                    string(name: 'BUILD_NUMBER', defaultValue: '', description: 'Number string for the build')
                    string(name: 'BUILD_VERSION', defaultValue: '', description: 'Version string for the build')
                    string(name: 'DISTRIBUTION_GROUPS', defaultValue: '', description: 'Comma seprated list of distribution Groups')
                }
            }
            steps {
                script { 
                    sh "appcenter distribute release -f $PATH_TO_BUILD --build-number $BUILD_NUMBER --build-version $BUILD_VERSION --group $DISTRIBUTION_GROUPS --app $APP_NAME --token $APPCENTER_API_TOKEN" 
                }

            }
        }
        stage('Test') {
            steps {
                sh 'appcenter apps list --token $APPCENTER_API_TOKEN'
            }
        }
        stage('Publish') {
            steps {
                echo "publish step"
//                sh 'appcenter distribute release -f emptyfile.dmg --build-number 1.0.1 --build-version 3.0 --group Collaborators --app T-Mobile-USA-Inc./BusinessHub-Connect-MacOS --token $APPCENTER_API_TOKEN' 
            }
        }
    }
}
