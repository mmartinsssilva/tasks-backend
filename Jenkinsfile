pipeline {
    agent any
    stages {
        stage ('Build Backend') {
            steps {
                sh 'mvn clean package -DskipTest=true'
            }    
        }
        stage ('teste unitario') {
            steps {
                sh 'echo teste'
            }    
        }
        stage ('Sonar Analysis') {
            environment {
                scannerHome = tool 'SONAR_SCANNER'
            }    
            steps {
                withSonarQubeEnv('SONAR_LOCAL') {
                sh "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=DeployBack -Dsonar.host.url=http://192.168.15.44:9000 -Dsonar.login=40127015afe3cb7da136aa3333dbdcbf94f86fe4 -Dsonar.java.binaries=target -Dsonar.coverage.exclusions=**/.mvn/**,**/src/test/**,**/model/**,**aplication.java"
                }
            }
        }
        stage ('Quality Gate') {  
            steps {
                timeout(time: 1, unit: 'MINUTES') {
                withForQualityGate abortPipeline: true 
                }
            }
        }          
    }
}
