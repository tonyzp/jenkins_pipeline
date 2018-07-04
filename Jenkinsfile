#!/usr/bin/env groovy

pipeline {
    agent any

    stages {
        stage('Build Driver') {
            steps {
                build job: 'Build-Driver', parameters: [string(name: 'project_build_mode', value: '测试环境'), [$class: 'GitParameterValue', name: 'project_branch_name', value: 'origin/dev']]
            }
        }
        stage('Build Consignor') {
            steps {
                build job: 'Build-Consignor', parameters: [string(name: 'project_build_mode', value: '测试环境'), [$class: 'GitParameterValue', name: 'project_branch_name', value: 'origin/develop']]
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
