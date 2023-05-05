//scripted pipeline
pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
			echo "Build"
			echo "PATH - $PATH"
			echo "BUILD_NUMBER - $env.BUILD_NO"
			echo "BUILD_TAG - $env.BUILD_TAG"
			echo "JOB_ID - $env.JOB_ID"
			echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Test'){
			steps{
			echo "Test"
			}
		}
	
		stage('Integration Test'){
			steps{
			echo "Integration Test"
			}
		}
	}

	post{
		always{
			echo "just check..."
		}
		success{
			echo "I am ok"
		}

		failure{
			echo "I am filed"
		}


	}
	
		
	
}