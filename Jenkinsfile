pipeline{
    agent any
    environment {
        SCA = '/var/lib/jenkins/dependency-check/bin/dependency-check.sh'
        }

    stages {
        stage('SCM') {
            steps {
                checkout scm //copia local codigo
            }
            
        }
    stage('BUILD') {
         steps {
            sh 'chmod +x mvnw'
            sh './mvnw clean install'
            }
        }

        stage('SAST') {
            steps {
			withSonarQubeEnv('sonar') {			
                sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast -Dsonar.host.url=https://sonarcloud.io -Dsonar.projectKey=3627839_spring-boot-kubernetes -Dsonar.organization=3627839'
            
                    }
        	    }	
	        
             }
	
	    stage ('SCA-DC') {  
		    steps { sh "$SCA --project 'tarea5' --failOnCVSS 7 --scan '${WORKSPACE}'/target/*.jar -o dependency-check-report.html"

		        }  
	        }  
    }
} 