pipeline {

    agent {label 'windows'}	
	
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
