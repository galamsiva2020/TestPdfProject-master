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
           stage('Maven Build') {
                steps{
                    sh "mvn -Dmaven.test.failure.ignore=true clean package"
                }
           }
           stage('Junit Test Reports'){
                steps{
                     junit '**/target/report.xml'
                     archiveArtifacts 'target/*.jar'
                }
           }
        }
}