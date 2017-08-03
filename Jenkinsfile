pipeline {
    agent { docker 'python:2.7.10' }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
    }
    post {
        success {
            slackSend channel: '#jenkins',
                      color: 'good',
                      message: "The pipeline ${currentBuild.fullDisplayName} completed successfully."
        }
        failure {
            slackSend channel: '#jenkins',
                      color: 'RED',
                      message: "The pipeline ${currentBuild.fullDisplayName} failed."
        }
        unstable {
            slackSend channel: '#jenkins',
                      color: 'RED',
                      message: "The pipeline ${currentBuild.fullDisplayName} is unstable."
        }
    }
}
