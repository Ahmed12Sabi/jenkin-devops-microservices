//scripted pipeline
pipeline{
	agent any
	stages{
		stage('Build'){
			steps{
			echo "Build"
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