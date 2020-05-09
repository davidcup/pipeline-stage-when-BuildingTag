pipeline {
    agent {label 'windows'}
	
    stages {
        stage('Build') {
		
			when{
				branch 'master'
			}
		
            steps {                
                echo 'Hello World building tag'
            }
        }
    }
}