pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'war', url: 'https://github.com/awskaizen02/feb-maven.git'
            }
        }
        stage('build') {
            steps {
                bat 'mvn clean'
                bat 'mvn install'
            }
        }
        stage('deployment') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tom', path: '', url: 'http://localhost:9999/')], contextPath: 'demo-pipleline', war: '**/*.war'
            }
        }

    }
}
