//scripted pipeline
pipeline{
	agent any

	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('checkout'){
			steps{
			sh 'mvn --version'
			sh 'docker --version'
			echo "Build"
			echo "PATH - $PATH"
			echo "BUILD_NUMBER - $env.BUILD_NO"
			echo "BUILD_TAG - $env.BUILD_TAG"
			echo "JOB_ID - $env.JOB_ID"
			echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('compile'){
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
			sh "mvn test"
			}
		}
	
		stage('Integration Test'){
			steps{
			sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package'){
			steps{
			sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image'){
			steps{
				//"docker build -t in28min/currency-exchange-devops:$env.BUILD_TAG"
				script{
					dockerImage=docker.build("ahmedsabiullah/currency-exchange-devops:${env.BUILD_TAG}") 				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
				docker.withRegistry(' ',dockerhub);
				dockerImage.Push();
				dockerImage.Push('latest');
				}
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