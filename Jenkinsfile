node{
      def mvnHome = tool name: 'maven 3.6.1', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/Admincssindiaonline/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
            sshagent(['944ecf8e-f06f-4478-a8b1-24c483a187dd']) {
               sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war ubuntu@http://3.106.56.70:/opt/apache-tomcat-8.5.45/webapps'
              
          }
         
     }
      
 }
