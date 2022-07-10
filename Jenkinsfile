pipeline{
    agent any
    environment {
        SCA = '/Users/opena/Downloads/DependencyCheck/bin/dependency-check.sh'
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
        /* 
        //stage('Check Quality Gate') {
        //    steps {	sleep(10)
		//        waitForQualityGate abortPipeline: true
		//        }
	    //}	
	   
       // stage ('Dependency-Check') {  
		//    steps { 
		//        sh "$SCA --project 't5-sca' --failOnCVSS 7 --scan '${WORKSPACE}'/target/*.jar -o dependency-check-report-T5.html"

		       } 
            }    
        } */
        stage('SAST') {
            steps {
            
			withSonarQubeEnv('sonar') {
			
                sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast -Dsonar.host.url=https://sonarcloud.io -Dsonar.projectKey=3627839_spring-boot-kubernetes -Dsonar.organization=3627839'
            
                    }
        	    }	
	        
    }
}