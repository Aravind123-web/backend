pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    stages {
        stage('TEST') {
            steps {
                sh """
                    echo "this is testing"
                """
            }
        }
    }
    post {
        always {
            echo 'I will always say hello again!'
            //deleteDir() // clean up our workspace
        }
        success {
            echo 'I will run when pipeline is successful!'
        }
        failure {
            echo 'I will run when pipeline fails!'
        }
    }
}