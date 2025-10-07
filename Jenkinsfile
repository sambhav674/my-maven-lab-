pipeline {
    agent any

    tools {
        maven 'MAVEN-HOME'
    }

    stages {
        stage('Welcome') {
            steps {
                echo "👋 Welcome to Jenkins Pipeline - Build #${env.BUILD_NUMBER}"
            }
        }

        stage('Clone & Clean') {
            steps {
                // Clean old workspace folder if it exists
                bat "rmdir /s /q my-maven-lab-" 
                bat "git clone https://github.com/sambhav674/my-maven-lab-.git"
                dir("my-maven-lab-") {
                    bat "mvn clean"
                }
            }
        }

        stage('Install') {
            steps {
                dir("my-maven-lab-") {
                    bat "mvn install"
                }
            }
        }

        stage('Test') {
            steps {
                dir("my-maven-lab-") {
                    bat "mvn test"
                }
            }
        }

        stage('Package') {
            steps {
                dir("my-maven-lab-") {
                    bat "mvn package"
                }
            }
        }
    }

    post {
        success {
            echo "🎉 Pipeline completed successfully!"
        }
        failure {
            echo "❌ Pipeline failed. Check console logs for details."
        }
    }
}
