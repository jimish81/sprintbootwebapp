pipeline {
 agent any
 tools {
  Maven 'maven'
  jdk 'java1.8.0'
 }
 stages {
  stage('Build') {
   steps {
    sh "mvn -B -DskipTests clean package"
   }
  }
  stage('Test') {
   steps {
    sh 'mvn test'
   }
  // post {
   // always {
    // junit 'target/surefire-reports/*.xml'
   // }
   //}
  }
    stage('Deploy') {
   steps {
    //sh 'java -jar target/sprintbootwebapp-0.0.1-SNAPSHOT.jar'
    sh "sudo docker build --tag=jendocker:sprintboot ."
    sh "sudo docker run --name=sprintboot -d -p 3030:3030 jendocker:sprintboot"
   }
  } 
//  stage('Publish') {
 // steps {
  //  sh 'curl -X PUT -u test:AP9FdXXr3Ger7RjvG5sDmMQRAPf -T target/sprintbootwebapp-0.0.1-SNAPSHOT.jar "http://35.200.190.192:8081/artifactory/mavenbuild/sprintbootwebapp-0.0.1-SNAPSHOT.jar"'
   //}
  //}

 }
}
