pipeline {
    agent {
        label 'master'
    }
    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        
  stage('SonarQube Analysis') {
    
      sh "mvn clean verify sonar:sonar -Dsonar.projectKey=applicationweb -Dsonar.projectName='applicationweb' -Dsonar.host.url=http://localhost:9009 -Dsonar.token=squ_211d2961113097411c91a0799ebdbd45dd2e462d"
  }
}
}
