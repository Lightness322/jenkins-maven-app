pipeline {
    agent any
    tools {
        maven 'maven-3.9'
    }
    stages {
        stage('build jar') {
            steps {
                sh 'mvn package'
            }
        }
        stage('build image') {
            steps {
                sh 'mvn package'
                withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASS', usernameVariable: 'USER')]) {
                    sh 'docker build -t lightness322/demo-app:jma-2.0 .'
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                    sh 'docker push lightness322/demo-app:jma-2.0'
                }
            }
        }
        stage('deploy') {
            steps {
                sh 'echo deploying'
            }
        }
    }
}
