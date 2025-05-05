pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.1.2'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    environment {
        NEW_VERSION = '1.3.0'
        SERVER_CREDENTIALS = credentials('server-credentials')
    }
    tools {
        maven "maven-3.9"
    }
    stages {
        stage('build') {
            steps {
                echo 'building app'
                echo "building version ${NEW_VERSION}"
            }
        }
        stage('tests') {
            steps {
                echo 'testing app'
            }
        }
        stage('build') {
            steps {
                echo "deploying with version param ${params.VERSION}"
                echo 'deploying app'
                echo "deploy with ${SERVER_CREDENTIALS}"
                sh "${SERVER_CREDENTIALS}"
                withCredentials([
                    usernamePassword(credentials: 'server-credentials', usernameVariable: USER, passwordVariable: PWD)
                ]) {
                    sh "some script ${USER} ${PWD}"
                }
            }
        }
    }
}
