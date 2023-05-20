currentBuild.displayName = "SonarQube-Project-#"+currentBuild.number

pipeline{
    agent any
    
    environment{
        PATH = "/opt/maven-3.9/bin:$PATH"
        }
  
    stages{     
       stage('GetCode'){
            steps{
                git 'git@github.com:tirusoma/javalogin.git'
            }
        }     
      
        stage("Maven Build"){
            steps{
                sh "mvn clean package"
            }
        }
		
	  stage('SonarQube analysis'){
//       def scannerHome = tool 'SonarScanner 4.0';

	      steps{
                 withSonarQubeEnv('sonarqube-9.1') { 
			  
                  // If you have configured more than one global server connection, you can specify its name
//                sh "${scannerHome}/bin/sonar-scanner"
      
                  sh "mvn sonar:sonar"
                }
            }
        }
       
    }
} 
