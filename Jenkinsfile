pipeline {
    agent {label 'windows'}
	
    stages {
        stage('Build') {
		
			when{
				tag "release-*"
			}
		
            steps {                
                echo 'Hello World building tag'
            }
        }
    }
}
