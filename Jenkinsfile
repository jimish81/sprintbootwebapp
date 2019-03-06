pipeline {
      environment {
    //login id/docker reposotory defined in Jenkins followe by repository name
    registry = "jimish22/jenkin-docker"
    //credential = Id given jenkins
    registryCredential = 'DockerHub'
    dockerImage = ''
    //checked if any container is running with same name node-app container Id will store same & stage cleanup will close that container
    containerId = sh(script: 'docker ps -aqf "name=node-app"', returnStdout: true)
  }    
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
      //  stage ('Test')
    //     {
           // steps
             // {
               // sh 'mvn test'
                //}
                //          post {
              //  always {
                //    junit 'target/surefire-reports/*.xml'
               // }
           // }
       //      }      
    stage('Building image') {
      steps{
        script {
          //will pisck registry from variable defined
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    

 }
}
