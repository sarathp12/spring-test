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

         stage ('build') { 
           steps {
            echo "i am running"
            sh 'mvn clean package'
            sh 'java -jar target/gs-spring-boot-0.1.0.jar'
             }
        }
            
     }
  }      
           
