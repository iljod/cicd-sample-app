pipeline {
    agent any

    triggers {
        pollSCM('* * * * *')  // Poll every minute
    }

    stages {
        stage('Preparation') {
            steps {
                catchError(buildResult: 'SUCCESS') {
                    sh 'docker stop samplerunning'
                    sh 'docker rm samplerunning'
                }
            }
        }
        stage('Build') {
            steps {
                build 'BuildSampleApp'
            }
        }
        stage('Results') {
            steps {
                build 'TestSampleApp'
            }
        }
    }
}
