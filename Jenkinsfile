pipeline {
      agent any
       tools {
         maven 'maven'
         
         }
     stages {
        stage("Git checkout"){
           steps{
              git branch: 'main', credentialsId: 'e44652ce-bc38-4e73-861a-f9dc731c2a27', url: 'https://github.com/Yogesh238/deploy.git'
              }
        }
        stage('Compile') {
            steps {
                sh 'mvn compile'
            }
        }   
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage("Package"){
           steps{
              sh "mvn package"
              }
              }
        stage("Install"){
           steps{
              sh "mvn install"
              }  
              }
         stage("Create War File"){
           steps{
              sh 'jar -cf target/my-app-1.0-SNAPSHOT.jar target/com.mycompany.app.App.war'
              } 
              }  
         stage("Deploy War File"){
           steps{
              sh "cp com.mycompany.app.App.war /home/ec2-user/apache-tomcat-8.5.61/webapps/"
              }   
          }
    }
}
