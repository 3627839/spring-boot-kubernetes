pipeline{
    agent any

    stages {
        stage('SCM1') {
            steps {
                checkout scm //copia local codigo
            }
            
        }

        stage('SAST1') {
            steps {
			//withSonarQubeEnv('sonarqube') {
			//	sh 'set +x; chmod 777 mvnw'
		    //    sh './mvnw clean package'
			//	sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast -Dsonar.host.url=https://sonarcloud.io -Dsonar.projectKey=3627839_spring-boot-kubernetes -Dsonar.organization=3627839'
            //    sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast -Dsonar.host.url=https://sonarcloud.io -Dsonar.projectKey=3627839_spring-boot-kubernetes -Dsonar.organization=3627839'
            	sh('set +x; ./mvnw sonarqube -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast -Dsonar.host.url=https://sonarcloud.io -Dsonar.projectKey=3627839_spring-boot-kubernetes -Dsonar.organization=3627839')
                    }
        	    }	
	        }
    }
