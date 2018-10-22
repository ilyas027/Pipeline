pipeline{
	agent any
	
	stages {
		stage ('Compile stage'){
			steps {
				withMaven(maven : 'maven_3.5.4') {
					bat 'mvn clean compile'
				}
			}
		}
			
		stage ('Testing Stage'){
			steps { 
				withMaven(maven : 'maven_3.5.4'){
					bat 'mvn test'
				}
			}
			
		}
		
		stage ('Deployment stage') {
			nexusPublisher nexusInstanceId: 'localnexus', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'war/target/jenkins.war']], mavenCoordinate: [artifactId: 'jenkins-war', groupId: 'org.jenkins-ci.main', packaging: 'war', version: '3.13']]]
			
		}
	
	}
}
