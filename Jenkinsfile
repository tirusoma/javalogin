pipeline{
    agent any
    environment {
        PATH = "$PATH:/opt/apache-maven-3.9/bin"
    }
    stages{
       stage('GetCode'){
            steps{
                git 'https://github.com/tirusoma/javalogin.git'
            }
         }        
       stage('build'){
          withMaven(maven: 'mvn') {
            sh "mvn clean package"
           }
        }
        stage('SonarQube analysis') {
//    def scannerHome = tool 'SonarScanner 4.0';
        steps{
        withSonarQubeEnv('sonarqube-8.9') { 
        // If you have configured more than one global server connection, you can specify its name
//      sh "${scannerHome}/bin/sonar-scanner"
        sh "mvn sonar:sonar"
    }
        }
        }
       
    }
} 
