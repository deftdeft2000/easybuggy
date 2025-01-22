pipeline {
    agent any

    environment {
        CHECKMARX_SERVER = 'https://your-checkmarx-server-url' // URL của Checkmarx server
        PROJECT_NAME = 'Your-Project-Name' // Tên dự án Checkmarx
        CHECKMARX_USERNAME = credentials('checkmarx-username') // Credential ID cho username
        CHECKMARX_PASSWORD = credentials('checkmarx-password') // Credential ID cho password
    }

    stages {
        stage('Checkout SCM') {
            steps {
                echo 'Checking out source code...'
                checkout scm
            }
        }

        stage('Scan with Checkmarx') {
            steps {
                echo 'Starting Checkmarx scan...'
                checkmarxASTScanner additionalOptions: '', baseAuthUrl: '', branchName: '', checkmarxInstallation: 'cxone', credentialsId: '', projectName: 'deftdeft2000/easybuggy', serverUrl: '', tenantName: ''
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            cleanWs()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed. Please check logs for more details.'
        }
    }
}
