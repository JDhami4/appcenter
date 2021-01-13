pipeline {
    agent any
    environment {
        APPCENTER_API_TOKEN = credentials('appcenter-api-token')
    }
    tools {nodejs "node"}
    
    stages {
        stage('Input parameters') {
            input {
                message 'Input Parameters?'
                ok 'Done!'
                parameters {
                    string(name: 'PATH_TO_BUILD', defaultValue: '', description: 'Path to the dmg file, relative to the root of the repo')
                    choice(name: 'APP_NAME', choices: ["prod","debug"], description: 'app name in app-center')
                }
            }
            steps {
                echo "${PATH_TO_BUILD} ${APP_NAME}"
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
//                sh 'appcenter distribute release -f emptyfile.dmg --build-number 1.0.1 --build-version 3.0 --group Collaborators --token $APPCENTER_API_TOKEN --app T-Mobile-USA-Inc./BusinessHub-Connect-MacOS' 
            }
        }
    }
}
