pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'building app'
            }
        }
        stage('tests') {
            steps {
                echo 'testing app'
            }
        }
        stage('build') {
            steps {
                echo 'deploying app'
            }
        }
    }
}
