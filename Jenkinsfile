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
  
    environment {
	  nuget = "c:/nuget"
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
		 script {
		 def MSBuild = tool 'MSBuild 2017'
	         bat "C:/Nuget/nuget.exe restore SchoolTracker.sln"
                 bat "\"${MSBuild}/msbuild\" /t:Build SchoolTracker.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
              }           
	   }
        }
    }
}
