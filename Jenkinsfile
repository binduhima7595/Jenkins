pipeline {
    agent any

    environment {
        PATH = "C:\\Windows\\System32;${env.PATH}"
    }

    stages {
        stage('Checkout Source') {
            steps {
                checkout([
                    $class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[
                        url: 'https://github.com/binduhima7595/Jenkins.git',
                        credentialsId: '8984cfd0-daed-4433-b4d1-f7b42c188c9e'
                    ]]
                ])
            }
        }

        stage('Run HelloWorld') {
            steps {
                script {
                    def isWindows = !isUnix()
                    if (isWindows) {
                        bat '''
                            if exist helloworld.py (
                                python helloworld.py
                            ) else (
                                echo File 'helloworld.py' not found. Skipping stage.
                                exit /b 1
                            )
                        '''
                    } else {
                        sh '''
                            if [ -f helloworld.py ]; then
                                python helloworld.py
                            else
                                echo "File 'helloworld.py' not found. Skipping stage."
                                exit 1
                            fi
                        '''
                    }
                }
            }
        }

        stage('Run HelloWipro') {
            steps {
                script {
                    def isWindows = !isUnix()
                    if (isWindows) {
                        bat '''
                            if exist hellowipro.py (
                                python hellowipro.py
                            ) else (
                                echo File 'hellowipro.py' not found. Skipping stage.
                                exit /b 1
                            )
                        '''
                    } else {
                        sh '''
                            if [ -f hellowipro.py ]; then
                                python hellowipro.py
                            else
                                echo "File 'hellowipro.py' not found. Skipping stage."
                                exit 1
                            fi
                        '''
                    }
                }
            }
        }

        stage('Run HelloJenkins') {
            steps {
                script {
                    def isWindows = !isUnix()
                    if (isWindows) {
                        bat '''
                            if exist hellojenkins.py (
                                python hellojenkins.py
                            ) else (
                                echo File 'hellojenkins.py' not found. Skipping stage.
                                exit /b 1
                            )
                        '''
                    } else {
                        sh '''
                            if [ -f hellojenkins.py ]; then
                                python hellojenkins.py
                            else
                                echo "File 'hellojenkins.py' not found. Skipping stage."
                                exit 1
                            fi
                        '''
                    }
                }
            }
        }
    }

    post {
        always {
            script {
                def isWindows = !isUnix()
                if (isWindows) {
                    bat '''
                        echo Build completed. Logging status...
                        echo Build completed at %DATE% %TIME% >> build_status.txt
                        echo Final workspace contents:
                        dir
                    '''
                } else {
                    sh '''
                        echo "Build completed. Logging status..."
                        echo "Build completed at $(date)" >> build_status.txt
                        echo "Final workspace contents:"
                        ls -l
                    '''
                }
            }
        }
        success {
            echo '✅ All scripts executed successfully.'
        }
        failure {
            echo '❌ One or more stages failed. Check logs for details.'
        }
    }
}