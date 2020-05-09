pipeline {

   agent {
    node {
      label 'windows'
      ////customWorkspace '/github-davidcup'
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

		    // PRINT ENVIRONMENT TO JOB
		   bat "echo 'Workspace is:' ${env.WORKSPACE}'"
		   bat "echo 'build URL is ${env.BUILD_URL}'"
		   bat "echo 'Folder name is:' ${env.JENKINS_HOME}'"
		   bat "echo 'Job name is:' ${env.JOB_BASE_NAME}'"			
		  
                }		    
            }
        }
    }
}
