node{
      stage('Checkout'){
         git 'https://github.com/Admincssindiaonline/java-tomcat-maven-example'
      }  
      stage('Build'){
         //// Get maven home path and build
        def mvnHome = tool name: 'Maven 3.6.1', type: 'maven'
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
      stage ('Test-JUnit'){
         def mvnHome = tool name: 'Maven 3.6.1', type: 'maven'
         sh "${mvnHome}/bin/mvn' test; sleep 3"
      }  
      stage('Deploy') {     
          sshagent(['8c1675a3-e2f2-4128-9b1e-deb0e4a4dd8c']) {
               sh 'scp -o StrictHostKeyChecking=no target/*.war root@3.106.56.70:/opt/apache-tomcat-8.5.45/webapps'
              
              }
               sh 'ssh -o StrictHostKeyChecking=no root@3.106.56.70 ${copyScript1}'
          }
      
     }
