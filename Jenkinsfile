#!/usr/bin/env groovy

pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                parallel build_driver: {
                    build job: 'Build-Driver', parameters: [string(name: 'project_build_mode', value: '测试环境'), [$class: 'GitParameterValue', name: 'project_branch_name', value: 'origin/dev']]
                },  build_consignor: {
                    build job: 'Build-Consignor', parameters: [string(name: 'project_build_mode', value: '测试环境'), [$class: 'GitParameterValue', name: 'project_branch_name', value: 'origin/develop']]
                }, failFast: true
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
