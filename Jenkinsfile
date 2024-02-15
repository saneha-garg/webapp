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

    stage('Test') {
      post {
        always {
          junit 'target/surefire-reports/*.xml'
        }

      }
      steps {
        bat 'mvn test'
      }
    }

    stage('Sonar-Report') {
      steps {
        bat 'mvn clean verify sonar:sonar -Dsonar.projectKey=applicationweb -Dsonar.projectName=\'applicationweb\' -Dsonar.host.url=http://localhost:9009 -Dsonar.token=squ_211d2961113097411c91a0799ebdbd45dd2e462d'
      }
    }

    stage('Deploy') {
      steps {
        // bat 'java -jar "C:\\Program Files\\Jenkins\\workspace\\webapplication\\target\\java-webapp-1.0.jar" '
       bat ' mvn clean package'
       bat ' java -jar target/java-webapp-1.0.jar '
      }
    }

  }
}
