pipeline {
    agent any

    tools {
        maven 'mvn'         // Must match the Maven tool name in Jenkins
        jdk 'JDK 9'         // Must match the JDK tool name in Jenkins
    }

    environment {
        JAVA_HOME = tool name: 'JDK 9', type: 'hudson.model.JDK'
        PATH = "${JAVA_HOME}/bin:${env.PATH}"
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
