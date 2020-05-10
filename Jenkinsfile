def branch='master'
pipeline {

   agent {
    node {
      label 'windows'
      customWorkspace 'C:/jenkins/workspace/github-davidcup'
    }
  }	
	
    stages {
	    stage('Checkout') {
          steps {                
                bat 'echo 'Hello'' 
			}
		}
        stage('Build') {
		
			when{
				branch 'master'
			}
		
            steps {
                timeout(time: 1, unit: 'MINUTES') {                      
                    bat 'mkdir dist\\\\windows' 
                }		    
            }
        }
    }
}
