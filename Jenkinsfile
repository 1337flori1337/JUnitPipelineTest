pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                echo("Building stage")
				
				// To run Maven on a Windows agent, use
				bat "mvn -Dmaven.test.failure.ignore=true clean package"
				
            }
        }
        stage('Test') { 
            steps {
                echo("Testing stage")
								
            }
			
			post {
					// If Maven was able to run the tests, even if some of the test
					// failed, record the test results and archive the jar file.
					success {
						echo("vor archive")
						
					   archive "target/**/*"
						
						
						echo("vor junit")
					   //junit '*/target/surefire-reports/TEST-.xml'
					   junit 'target/surefire-reports/*.xml'
					   
					   //echo("vor artifacts")
					   //archiveArtifacts 'target/*.jar'
					   
					   
					   echo("success")
					}
				}
			
        }
        stage('Deploy') { 
            steps {
                echo("Deploying stage") 
            }
        }
    }
}
