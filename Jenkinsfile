pipeline{
    agent any
    stages {
        stage('SCM') {
            steps {
                checkout scm
            }
        }
        stage('SAST') {
            steps {
                echo '=============================== SAST ==============================='
                sh 'chmod +x grandlew'
                sh './gradlew sonarqube -Dsonar.login=28d69acf9830970cfbd714342091af6783a02e7b -Dsonar.branch.name=t4-sast'
            }
        }
    }
}