node{
      def mvnHome = "/home/jawwad/apache-maven-3.6.2"
      stage('Checkout'){
         git 'https://github.com/jawwadmohammad/maven_tomcate'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') { 
            agent {
        node {
          label "master"
               cp ~/.jenkins/workspace/tomcate_pipeline/target/tomcatdeploymnetdemo.war jawwad@192.168.112.131:/home/jawwad/apache-tomcat-8.0.53/webapps'
              
          }
         
     }
      
 }
}
