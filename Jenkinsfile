def getFolderName() {
    def array = pwd().split("/")
    return array[array.length - 2];
}

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
			 def foldername = getFolderName()
		   bat "${foldername}"
                }		    
            }
        }
    }
}
