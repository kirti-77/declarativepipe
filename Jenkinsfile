pipeline {
  agent any
  stages {
		stage('Maven Compile'){
			steps{
				echo 'Project compile stage'
				bat label: 'Compilation running', script: '''mvn compile'''
      }
}
 
stage('Unit Test') {
  		steps {
			echo 'Project Testing stage'
			bat label: 'Test running', script: '''mvn test'''
       
       }
   }
   
   stage('Jacoco'){
     steps{
      jacoco()
     }
   }
   
stage('SonarQube'){

			steps{

				bat label: '', script: '''mvn sonar:sonar \

				-Dsonar.host.url=http://localhost:9000 \

				-Dsonar.login=squ_c4f54ffaef4d2c21303ebd66796d5139526dd8a4'''

                }

   } 
 
stage('Maven Package'){

		steps{

			echo 'Project packaging stage'
			bat label: 'Project packaging', script: '''mvn package'''
			}
		} 

post {
       always {
           cucumber '**/cucumber.json'
       }
   }
  

}