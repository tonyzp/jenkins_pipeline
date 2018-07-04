#!/usr/bin/env groovy

pipeline {
    agent any

    stages {
        stage('Build Job 1') {
            steps {
                build 'example-job1'
            }
        }
        stage('Build Job 2') {
            steps {
                build 'example-job2'
            }
        }
    }

    post {
        success {
            echo 'All pipeline stages succeed!'
        }
        failure {
            echo 'Pipeline stages failed!'
        }
    }
}
