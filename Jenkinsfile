pipeline {
    agent any

    stages {
        stage('Debug Environment') {
            steps {
                echo 'Checking Python availability and workspace...'
                sh '''
                    echo Current directory: $(pwd)
                    echo Python version:
                    python --version
                '''
            }
        }

        stage('Run HelloWorld') {
            steps {
                echo 'Running helloworld.py...'
                sh 'python helloworld.py'
            }
        }

        stage('Run HelloWipro') {
            steps {
                echo 'Running hellowipro.py...'
                sh 'python hellowipro.py'
            }
        }

        stage('Run HelloJenkins') {
            steps {
                echo 'Running hellowjenkins.py...'
                sh 'python hellowjenkins.py'
            }
        }
    }

    post {
        always {
            echo 'Build completed. Logging status...'
            sh 'echo Build completed at $(date) >> build_status.txt'
        }
        success {
            echo 'All scripts ran successfully!'
        }
        failure {
            echo 'One or more scripts failed.'
        }
    }
}