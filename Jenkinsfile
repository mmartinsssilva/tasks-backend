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
                sleep(5)
                timeout(time: 1, unit: 'MINUTES') {
                    waitForQualityGate abortPipeline: true 
                }
            }
        } 
        stage ('Deploy Backend') {  
            steps {
                sleep(5)
                //linha deploy
            }
        }  
        stage ('API TEST') {  
            steps {
                dir('api-test') {
                git credentialsId: 'github_login1', url: 'https://github.com/mmartinsssilva/tasks-api-test'
                //sh 'mvn test'
                }
            }
        } 
        stage ('Deploy Frontend') {  
            steps {
                dir('frontend') {
                git credentialsId: 'github_login1', url: 'https://github.com/wcaquinocursos/tasks-frontend'
                sh 'mvn clean package '
                //linha do deploy
                }
            }
        }
        stage ('Funtional  TEST') {  
            steps {
                dir('funtional-test') {
                git credentialsId: 'github_login1', url: 'https://github.com/mmartinsssilva/tasks-api-test'
                //sh 'mvn test'
                }
            }
        }                  
    }
}

