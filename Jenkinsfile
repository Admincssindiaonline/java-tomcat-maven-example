node{
      stage('Checkout'){
         git 'https://github.com/Admincssindiaonline/java-tomcat-maven-example'
      }  
      stage('Build'){
         //// Get maven home path and build
         def mvnHome = tool name: 'Maven 3.6.1', type: 'maven'
         sh "${mvnHome}/bin/mvn package"
      }
      stage ('Test'){
         def mvnHome = tool name: 'Maven 3.6.1', type: 'maven'
         sh "${mvnHome}/bin/mvn test; sleep 3"
      }  
      stage('Deploy') {     
           sshagent(['944ecf8e-f06f-4478-a8b1-24c483a187dd']) {
                 sh 'scp -o StrictHostKeyChecking=no target/*.war root@3.106.56.70:/opt/apache-tomcat-8.5.45/webapps'
           }
           /*sshagent{['944ecf8e-f06f-4478-a8b1-24c483a187dd']){
                 sh 'ssh -o StrictHostKeyChecking=no target/*.war root@3.106.56.70 ${copyScript1}'
         
         }
         */
    }
