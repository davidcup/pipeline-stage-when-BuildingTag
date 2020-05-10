pipeline {

   agent {
    node {
      label 'windows'
      customWorkspace 'C:/jenkins/workspace/github-davidcup'
    }
  }	
	
    stages {
        stage('Build') {
		
			when{
				branch 'master'
			}
		
            steps {                
                cleanWs()
                timeout(time: 1, unit: 'MINUTES') {                      
                    bat 'mkdir dist\\\\windows' 
                }		    
            }
        }
    }
}
