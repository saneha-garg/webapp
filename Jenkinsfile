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
  //       stage('Sonar-Report') {
  //           steps {
  //           sh 'mvn sonar:sonar \
  // -Dsonar.projectKey=jenkins_project \
  // -Dsonar.host.url=http://169.254.36.199:9000 \
  // -Dsonar.login=sqa_56e4aa4aa6823c3d35f69632632744afd19bdd91
  //           }
  //       }
        stage('Test') { 
            steps {
                bat 'mvn test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
        stage('Sonar-Report') {  
           steps { 
                bat 'mvn clean install sonar:sonar -Dsonar.host.url=http://169.254.36.199:9000 -Dsonar.analysis.mode=publish'  
            }
    }
}
}
