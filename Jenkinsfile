pipeline {
    
    agent {
      label 'centos7-slave'
      }

    tools {
       maven 'maven'
       jdk 'jdk'
     }
    stages {
         
         stage ('compile') {
           steps {
             sh 'mvn compile'
             }
        }

         stage ('Static Analysis') {
           steps {
             sh 'mvn sonar:sonar -Dsonar.host.url=http://192.168.199.133:9000 -Dsonar.jdbc.url=jdbc:postgresql://192.168.199.133/sonar'
            } 
        }

         stage ('build') { 
           steps {
            echo "i am running"
            sh 'mvn clean package'
            sh 'java -jar target/gs-spring-boot-0.1.0.jar'
             }
        }
            
     }
  }      
           
