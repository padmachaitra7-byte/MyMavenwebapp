pipeline {
    agent any  

    tools {
        maven 'Maven'  
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/padmachaitra7-byte/MyMavenwebapp.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', fingerprint: true
            }
        }

        stage('Deploy') {
            steps {
                sh 'cp target/*.war /opt/tomcat/webapps/'
            }
        }    
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
