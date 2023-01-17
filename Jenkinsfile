pipeline {
    agent any
    environment {
        CI = 'true'
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                snykSecurity(
                snykInstallation: 'infoSecProject',
                snykTokenId: 'snykToken',
                // place other optional parameters here, for example:
                failOnIssues: "false"
                )
            }
        }
        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                input message: 'Satisfied? (Press enter to exit)'
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
