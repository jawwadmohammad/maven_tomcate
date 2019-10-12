node{
      def mvnHome = tool name: 'maven 3.5.4', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
            sshagent(['32a77e75-021c-4e18-819a-f04bd5f8359d']) {
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war jawwad@192.168.112.131:/home/jawwad/apache-tomcat-8.0.53/webapps'
              
          }
         
     }
      
 }
