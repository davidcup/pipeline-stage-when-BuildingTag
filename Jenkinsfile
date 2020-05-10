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
		  
			when{
				branch 'master'
			}
		
          steps {                
                timeout(time: 1, unit: 'MINUTES') {                      
                    bat 'echol "Hello"' 
                }
			}
		}
        stage('Build') {
		
            steps {
                timeout(time: 1, unit: 'MINUTES') {                      
                    bat 'mkdir dist\\\\windows' 
                }		    
            }
        }
    }
}
