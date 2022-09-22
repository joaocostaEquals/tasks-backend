pipeline {
    agent any
    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean package -DskipTests=true'
            }
        }
        stage ('Tests'){
            steps {
                sh 'mvn test'
            }
        }
        stage ('Sonar Analysis'){
            environment {
                scannerHome = tool 'sonar_scanner'
            }
            steps {
                withSonarQubeEnv('sonar'){
                    sh "${scannerHome}/bin/sonar-scanner -e -Dsonar.projectKey=CICD -Dsonar.host.url=http://sonarqube:9000 -Dsonar.login=14d583af6c45fe7abab4a6d26a4daa325fe8bd28 -Dsonar.java.binaries=target"
                }
            }
        }
    }
}

