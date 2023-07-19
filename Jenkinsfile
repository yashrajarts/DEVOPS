pipeline {
    agent any
    
    tools {
        maven 'Maven'
    }

stages{
        stage('Build'){
            steps {
                bat 'maven clean package'
            }
            post {
                success {
                    echo 'Archiving the artifacts'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments'){
            steps {
                        deploy adapters: [tomcat9(credentialsId: 'e0050683-5390-49d1-a840-65bde1940406', path: '', url: 'http://localhost:8005/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
