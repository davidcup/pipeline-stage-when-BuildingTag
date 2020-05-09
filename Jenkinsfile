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
			def buildNumber = env.BUILD_NUMBER
		    def workspace = env.WORKSPACE
		    def buildUrl = env.BUILD_URL

		    // PRINT ENVIRONMENT TO JOB
		   bat 'echo "workspace directory is ${workspace}"'
		   bat 'echo "build URL is ${env.BUILD_URL}"'
                }		    
            }
        }
    }
}
