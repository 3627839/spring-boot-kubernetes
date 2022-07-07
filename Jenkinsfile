pipeline{
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout scm //copia local codigo
            }
        }
       
        stage('SAST1') {
            steps {
			withSonarQubeEnv('sonar') {
	//			sh 'set +x; chmod 777 mvnw'
	//	                sh './mvnw clean package'
				sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast -Dsonar.host.url=https://sonarcloud.io -Dsonar.projectKey=3627839_spring-boot-kubernetes -Dsonar.organization=3627839'
				}
        	    	}	
	        }	

       // stage('SAST') {
            //steps {
           //     echo '=============================== SAST ==============================='
            //    sh 'chmod +x gradlew'
          //      sh './gradlew sonarqube -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast'
        //    }
      //  }
    }
}