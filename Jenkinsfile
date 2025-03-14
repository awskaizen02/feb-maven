pipeline {
    agent any
    parameters {
     choice(name: 'BRANCHES', choices: ['war', 'jar', 'master'], description: '')  }
    triggers { cron('H/05 * * * *')     }
    

    stages {
        stage('SCM') {
            steps {
                git branch: "${params.BRANCHES}", url: 'https://github.com/awskaizen02/feb-maven.git'
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

