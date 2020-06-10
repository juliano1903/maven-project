pipeline {
    agent any
    tools {
        maven 'Maven Local' 
    }
    stages{
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
        stage('Deploy to staging') {
            steps {
                build job: 'first-maven-project-deploy-staging'
            }
        }
    }
}