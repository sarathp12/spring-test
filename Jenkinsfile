pipeline {
    
    agent {
      label 'centos7-slave'
      }

    tools {
       maven 'maven'
       jdk 'jdk'
     }
    stages {
         
         stage ('Checkout external proj') {
          
           steps {
               git branch: 'master',
                credentialsId: 'sarathp',
                url: 'https://github.com/sarathp12/spring-test.git'
             }
        }
        
         stage ('compile') {
           steps {
             sh 'mvn compile'
             }
        }

         stage ('Static Analysis') {
           steps {
             sh 'mvn sonar:sonar -Dsonar.host.url=http://$(boot2docker ip):9000 -Dsonar.jdbc.url=jdbc:postgresql://$(boot2docker ip)/sonar'
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
           
