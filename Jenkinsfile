pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            steps {
                sh 'mvn clean package -DskipTest=true'
            }    
        }
        stage ('meio') {
            steps {
                sh 'echo meio'
            }    
        }
        stage ('fim') {
            steps {
                sh 'echo fim'
            }
        }         
    }
}
