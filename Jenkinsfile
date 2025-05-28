pipeline {
    agent any

    tools {
        maven 'mvn'         // 👈 Must match the name in Jenkins
        jdk 'JDK 9'         // 👈 Must match the name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: '5f05146f-90ff-4919-b2f7-8cc9690c356c', url: 'https://github.com/rajayush808/mymavenapp.git'
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
        }

        stage('Package') {
            steps {
                sh 'mvn package'
            }
        }
    }

    post {
        success {
            echo '✅ Build and test successful!'
        }
        failure {
            echo '❌ Build or test failed.'
        }
    }
}
