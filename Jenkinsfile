pipeline {
    agent any
    
    tools {
        maven 'Maven'
    }
    
stages{
        stage('Build'){
            steps {
                bat 'mvn clean install'
            }

        stage ('Deployments'){
            steps {
                        deploy adapters: [tomcat9(credentialsId: 'e0050683-5390-49d1-a840-65bde1940406', path: '', url: 'http://localhost:8005/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
