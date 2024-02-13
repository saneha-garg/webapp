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
  -Dsonar.login=squ_211d2961113097411c91a0799ebdbd45dd2e462d'
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
         stage('Sonar-publish') {  
            steps { 
                 bat 'mvn clean install sonar:sonar -Dsonar.host.url=http://localhost:9009 -Dsonar.analysis.mode=publish'  
             }
      }
        // stage('Deploy'){
        //     steps{
        //         bat '/var/deployment/./deployment.sh'
        //     }
        // }
}
}
