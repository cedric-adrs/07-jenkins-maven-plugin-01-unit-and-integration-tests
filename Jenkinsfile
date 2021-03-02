pipeline {
    agent any
    
    tools {
        maven 'my-maven-3' 
    }
    
    stages {
    	 
	//    stage ('Clone') {
    //         steps {
    //             git branch: 'main', url: "https://github.com/cedric-adrs/07-jenkins-maven-plugin-01-unit-and-integration-tests"
    //         }
	//     }
	 
	   stage('Build & Unit test'){
		  steps {
				sh 'mvn clean verify -DskipITs=true';
		      	junit '**/target/surefire-reports/TEST-*.xml'
		      	archiveArtifacts  'target/*.jar'

	      }
   	  }
	
	  stage ('Integration Test'){
	      steps {
    			sh  'mvn clean verify -Dsurefire.skip=true';
				junit '**/target/failsafe-reports/TEST-*.xml'
      			archiveArtifacts  'target/*.jar'
      		}
      }	
    }
  }