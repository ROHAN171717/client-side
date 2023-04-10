pipeline {
    agent any
    options {
        skipStagesAfterUnstable()
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('DockerHub')
    }
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build') { 
            steps { 
                sh 'docker build -t rohanlakhani1717/mern-app:latest .'
            }
        }
        stage('Login'){
            steps {
                sh 'docker login -u  $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push rohanlakhani1717/mern-app:latest'
            }
        }
    }
}