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
        node {
  stage('SCM') {
    checkout scm
  }
  stage('SonarQube Analysis') {
    def mvn = tool 'Default Maven';

      sh "${mvn}/bin/mvn clean verify sonar:sonar -Dsonar.projectKey=applicationweb -Dsonar.projectName='applicationweb' -Dsonar.token=squ_211d2961113097411c91a0799ebdbd45dd2e462d"
  }
}
    }
}
