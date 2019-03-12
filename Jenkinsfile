node{
   stage('SCM Checkout'){
     git 'https://github.com/duvva123/war.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome = tool name: 'maven-3', type: 'maven'
      sh "${mvnHome}/usr/share/maven"
   }
   stage('Deploy to Tomcat'){
      sshagent(['tomcat-dev']) {
          sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@3.94.113.106:/var/lib/tomcat8/webapps/'
      }
   }
