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
                cleanWs()
				checkout(
                  [ $class: 'GitSCM',
                    branches: [[name: "refs/heads/${env.BRANCH_NAME}"]],
                    extensions: [
                      [ $class: 'CloneOption', depth: 1, honorRefspec: true, noTags: true, reference: 'davidcup/pipeline-stage-when-buildingtag', shallow: true],
                      [ $class: 'LocalBranch', localBranch: env.BRANCH_NAME],
                      [ $class: 'PruneStaleBranch']
                    ],
                    gitTool: scm.gitTool,
                    userRemoteConfigs: [
                      [ refspec: scm.userRemoteConfigs[0].refspec,
                        url: scm.userRemoteConfigs[0].url
                      ]
                    ]
                  ]
                )
			}
		}
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
