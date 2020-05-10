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
    
		    dir("${branch}") {
		      checkout([$class: 'GitSCM',
				userRemoteConfigs: [[name: 'bugs-origin-subdir',
						     refspec: "+refs/heads/${branch}:refs/remotes/bugs-origin-subdir/${branch}",
						     url: 'https://github.com/davidcup/pipeline-stage-when-BuildingTag.git']],
				branches: [[name: "${branch}"]],
				browser: [$class: 'GithubWeb', repoUrl: 'https://github.com/davidcup/pipeline-stage-when-BuildingTag.git'],
				extensions: [
				  [$class: 'AuthorInChangelog'],
				  [$class: 'CleanBeforeCheckout'],
				  [$class: 'CloneOption', honorRefspec: true, noTags: true, reference: '../.git', shallow: true],
				  [$class: 'LocalBranch', localBranch: "${branch}"],
				],
			       ])
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
