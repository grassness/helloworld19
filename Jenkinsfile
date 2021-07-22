pipeline {
    agent any
    triggers {
        pollSCM '* * * * *'
    }

    environment {
        registry = "grassness/devop-pipeline"
        registryCredential = "DockerID"
    }
    tools {
        maven 'M2_HOME'
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
