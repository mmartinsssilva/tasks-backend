pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            steps {
                sh 'mvn clean package -DskipTest=true'
            }    
        }
        stage ('unit test') {
            steps {
                sh 'mvn test'
            }    
        }   
        }
        stage ('fim') {
            steps {
                sh 'echo fim'
            }
        }         
    }
}