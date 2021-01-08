pipeline{
    agent any
        tools {
            // Install the Maven version configured as "M3" and add it to the path.
            maven "M3"
        }
        stages{
           stage ('Git Checkout'){
                steps{
                checkout scm
                }
           }

		stage('Maven Build'){
		steps{
		    sh '${MAVEN_HOME}/bin/mvn -B verify'
           }
			}

		stage('JunitTestResults') {
		steps{
	        junit '**/target/surefire-reports/TEST-*.xml'
              archiveArtifacts 'target/*.jar'
			  }
        }
}