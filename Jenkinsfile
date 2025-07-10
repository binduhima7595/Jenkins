pipeline {
    agent any

    stages {
        stage('Debug Environment') {
            steps {
                echo 'Checking Python availability and workspace...'
                bat '''
                    echo Current directory: %cd%
                    echo Python version:
                    python --version
                '''
            }
        }

        stage('Run HelloWorld') {
            steps {
                echo 'Running helloworld.py...'
                bat 'python helloworld.py'
            }
        }

        stage('Run HelloWipro') {
            steps {
                echo 'Running hellowipro.py...'
                bat 'python hellowipro.py'
            }
        }

        stage('Run HelloJenkins') {
            steps {
                echo 'Running hellowjenkins.py...'
                bat 'python hellowjenkins.py'
            }
        }
    }

    post {
        always {
            echo 'Build completed. Logging status...'
            bat 'echo Build completed at %date% %time% >> build_status.txt'
        }
        success {
            echo 'All scripts ran successfully!'
        }
        failure {
            echo 'One or more scripts failed.'
        }
    }
}