pipeline {
    agent none
    tools  {
      maven 'maven'
      jdk 'jdk'
      }

    stages {
         stage ('build') { 
         agent {
           label 'centos7-slave'
         }
          steps {
            checkout scm
            echo "i am running"
            sh 'mvn clean package'
            sh 'java -jar target/gs-spring-boot-0.1.0.jar'
             }
         }
             
      }
  }      
           
