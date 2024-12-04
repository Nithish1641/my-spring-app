pipeline {
    agent any

    tools {
        maven 'Default'  // Use the Maven configured in Jenkins
        jdk 'Default'   // Use the default JDK configured in Jenkins
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url: 'https://github.com/your-repo/my-spring-app.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }

            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy step here. (e.g., SCP, FTP, Kubernetes, Docker)'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }

        failure {
            echo 'Pipeline failed. Please check logs.'
        }
    }
}
