pipeline {
  agent any
  tools {
      maven 'maven3.6.0'
      jdk 'java1.8.0'
    }
    stages 
    {
      stage('Build') 
      {
       steps 
       {
        sh "mvn -B -DskipTests clean package"
        }
      }
         stage ('Test')
           {
            steps
               {
                sh 'mvn test'
                }
                            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
             }      
        stage('Publish') {
   steps {
    sh 'curl -X PUT -u jimish:APARmshG1mhGExY41HfTjXX5Z8x -T target/sprintbootwebapp-0.0.1-SNAPSHOT.jar "http://18.236.125.160:8081/artifactory/libs-release/my-app-1.0-SNAPSHOT.jar"'
   }
  }
         stage ('Deploy')
       {
      steps
      {
       sh "sudo docker build --tag=jenkin-docker:springboot ."
       sh "sudo docker run --name=springboot -d -p 9001:9001 jenkin-docker:springboot"
      }
      }


 }
}
