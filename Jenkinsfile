pipeline {
    agent {
        label 'AGENT-1'
    }
    options {
        timeout(time: 30, unit: 'MINUTES')
        disableConcurrentBuilds()
        ansiColor('xterm') // to display colored output in the console logss
    }
    environment {
        def appVersion = '' // varaiable declaration
    }
    stages {
        stage('read the version') { // stage to read the version from package.json file and store it in a variable
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    appVersion = packageJson.version
                    echo "The application version is: $appVersion"
                }
            }
        }
        stage('Install Dependencies') { // stage to install the dependencies and display the version in the console logs
            steps {
                sh """
                npm install
                ls -ltr
                echo "The application version is: $appVersion"
                """
            }
        }
        // stage('Build') { // stage to build the application
        //     steps {
        //         sh """
        //         zip -q -r backend-${appVersion}.zip * -x Jenkinsfile -x backend-${appVersion}.zip
        //         ls -ltr
        //         """
        //     }
        // }
    }
    post {
        always {
            echo 'I will always say hello again!'
           // deleteDir() // clean up our workspace
        }
        success {
            echo 'I will run when pipeline is successful!'
        }
        failure {
            echo 'I will run when pipeline fails!'
        }
    }
}