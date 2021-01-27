pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            steps {
                sh 'mvn clean package -DskipTest=true'
            }    
        }
        stage ('Unit test') {
            steps {
                sh 'echo test'
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
