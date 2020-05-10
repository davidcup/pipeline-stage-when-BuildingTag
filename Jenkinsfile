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
	  Nuget = "C:/Nuget"
	}
	
    stages {
	stage('Checkout') {		  
		when {
		  branch 'master'
		}		
		  steps {                
			timeout(time: 1, unit: 'MINUTES') {                      
			    bat 'echo "Hello"' 
				script{
					def isMainlineBranch = (env.BRANCH_NAME ==~ /master|next|\d_\d_(X|\d)/)
					def targetBranch = env.CHANGE_TARGET 
					if (isMainlineBranch) { 
						targetBranch = env.BRANCH_NAME
					}
					if (!targetBranch) { 
						targetBranch = 'master'
					}
					bat "echo The main is ${env.BRANCH_NAME}"
					bat "The target is ${env.CHANGE_TARGET}"
				}
		      }
	     }
	}
        stage('Build') {		
            steps {
		 script {
		 def MSBuild = tool 'MSBuild 2017'
	         bat "${env.Nuget}/nuget.exe restore SchoolTracker.sln"
                 bat "\"${MSBuild}/msbuild\" /t:Build SchoolTracker.sln /p:Configuration=Release /p:Platform=\"Any CPU\" /p:ProductVersion=1.0.0.${env.BUILD_NUMBER}"
              }           
	   }
        }
    }
}
