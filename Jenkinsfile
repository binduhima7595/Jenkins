pipeline {
    agent any

    stages {
        stage('Debug Environment') {
            steps {
                echo 'Checking Python availability and shell environment...'
                script {
                    def output = sh(
                        script: '''
                            echo "Current working directory:"
                            pwd

                            echo "Shell PATH:"
                            echo "$PATH"

                            echo "Trying to locate python..."
                            which python || echo "Python not found"

                            echo "Trying to run 'python --version'..."
                            python --version || echo "Unable to execute python"

                            echo "Listing workspace contents..."
                            ls -l
                        ''',
                        returnStdout: true
                    ).trim()
                    echo "Debug Output:\n${output}"
                }
            }
        }
    }

    post {
        always {
            echo 'Build completed.'
        }
        success {
            echo 'Environment diagnostics completed successfully.'
        }
        failure {
            echo 'Diagnostics failed. Check Debug Output for details.'
        }
    }
}
