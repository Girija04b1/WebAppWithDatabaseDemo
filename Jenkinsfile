pipeline {
    agent {
        docker {
            image 'jenkins/agent'
            label 'docker-agent'
            }
    }
    stages {
        stage('Clone repository') {
            steps {
                git 'https://github.com/HoussemDellai/WebAppWithDatabaseDemo.git'
                }
        }
        stage('Run SonarScanner') {
            steps {
                sh 'docker run -ti -v ./:/root/src --link sonarqube sonarsource/sonar-scanner-cli -D sonar.host.url=http://sonarqube:9000 -D sonar.scm.provider=git -D sonar.projectBaseDir=/root/src -D sonar.sources=. -D sonar.projectName=dotnetcore_demo_sonar -D sonar.token=squ_30dbe20534473e88792eb94c3c55efdb5dfa04f9 -D sonar.projectKey=dotnetcore_demo_sonar'
            }
        }
    }
}
