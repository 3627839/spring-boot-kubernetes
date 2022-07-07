pipeline{
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout scm //copia local codigo
            }
        }
             stage('BUILD') {
                steps {
                echo '=============================== BUILD ==============================='
                echo ''
                sh 'chmod 777 mvnw'
                sh './mvnw clean build'
            }
        }
        
     //   stage('SAST') {
     //    steps {
     //       echo '=============================== SAST ==============================='
     //       echo ''
     //       sh('set +x; ./mvnw sonarqube -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast')
     //    }
     // }

      stages {
        stage('SAST') {
            steps {
			withSonarQubeEnv('sonar') {
				sh 'set +x; chmod 777 mvnw'
		        sh './mvnw clean package'
				sh './mvnw org.sonarsource.scanner.maven:sonar-maven-plugin:sonar -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast -Dsonar.host.url=https://sonarcloud.io -Dsonar.projectKey=3627839_spring-boot-kubernetes -Dsonar.organization=3627839'
				}
        	    	}	
	        }
    }
}