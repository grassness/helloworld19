pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }
    tools {
        maven 'M2_HOME'
    }
    environment {
        registry = "grassness/development1-pipeline"
        registryCredential = 'DockerID'
    }
    stages {
        stage('build') {
            steps{
            sh 'mvn clean'
            sh 'mvn install'
            sh 'mvn package'
           
            }
        }

        stage('test'){
            steps {
                echo "test step"
                sh 'mvn test'
            }
        }
        stage ('Deploy') {
            steps {
                script {
                    docker.build registry = ":$BUILD_NUMBER"
                }
            }
        }    
        
    }
}
