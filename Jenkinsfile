pipeline {
    agent any

    stages {
        stage('Debug Environment') {
            steps {
                echo 'Checking Python availability and shell environment...'
                sh '''
                    echo "Current working directory:"
                    pwd

                    echo "Shell PATH:"
                    echo "$PATH"

                    echo "Trying to locate python..."
                    which python || echo "Python not found in PATH"

                    echo "Trying to run 'python --version'..."
                    python --version || echo "Unable to execute python"

                    echo "Listing workspace contents..."
                    ls -l
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
            sh '''
                echo "Build completed at $(date)" >> build_status.txt
                echo "Final workspace contents:"
                ls -l
            '''
        }
        success {
            echo 'All scripts executed successfully.'
        }
        failure {
            echo 'One or more stages failed. Check logs for details.'
        }
    }
}