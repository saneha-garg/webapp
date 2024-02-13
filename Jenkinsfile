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
          stage('Sonar-Report') {
            steps {
            bat 'mvn sonar:sonar \
  -Dsonar.projectKey=jenkins_project \
  -Dsonar.host.url=http://localhost:9009 \
  -Dsonar.login=squ_e16631c55d56e72378e1841bf14f3676e5b226dc'
            }
        }
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
      //    stage('Sonar-Report') {  
      //       steps { 
      //            bat 'mvn clean install sonar:sonar -Dsonar.host.url=http://localhost:9009 -Dsonar.analysis.mode=publish'  
      //        }
      // }
        // stage('Deploy'){
        //     steps{
        //         bat '/var/deployment/./deployment.sh'
        //     }
        // }
}
}
