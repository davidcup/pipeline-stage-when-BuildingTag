pipeline {

   options { 
      disableConcurrentBuilds() 
	  buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '5'))
	}

   agent {
    node {
      label 'windows'
      customWorkspace 'C:/jenkins/workspace/github-davidcup'
    }
  }	
	
    stages {
	    stage('Checkout') {
		  
			when{
				branch 'master'
			}
		
          steps {                
                timeout(time: 1, unit: 'MINUTES') {                      
                    bat 'echo "Hello"' 
                }
			}
		}
        stage('Build') {
		
            steps {
                bat "\"${tool 'MSBuild 2017'}\" SchoolTracker.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
            }
        }
    }
}
