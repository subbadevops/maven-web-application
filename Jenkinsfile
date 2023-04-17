node ('Java_node1'){

def MavenHome=tool name= "Maven_3.9.1"
    
    properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '5', artifactNumToKeepStr: '5', daysToKeepStr: '5', numToKeepStr: '5')), pipelineTriggers([cron('* * * * *')])])
    stage('CheckoutCodeFromGitHub') 
                    {
git credentialsId: '045deed1-c6ee-4287-b4ba-6082b2610a6c', url: 'https://github.com/DevOps-Rjpt-2022/maven-web-application.git'
                     }
    stage('BuildArifact')
     {
  sh "${MavenHome}/bin/mvn clean package"
     }
     //Below stage for uploading artifcats into sonarqube
     /*
stage('SonarQubeReport')
     {
  sh "${MavenHome}/bin/mvn sonar:sonar"
     }
stage('DeployToNexus')
     {
  sh "${MavenHome}/bin/mvn clean deploy"
     }
stage('DeployToTomcat')
    {
sshagent(['520a8fe2-9c33-4337-b92f-2a53c5189336']) {
sh " scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@15.206.117.30:/opt/apache-tomcat-9.0.73/webapps/"
}
    }
    */
stage('MailNotification')
{
emailext body: '''Build got completed here is the status.

Regards,
jeevan''', subject: 'Build Status', to: 'djeevand12@gmail.com veera@gmail.com priyanka@gmail.com vinay@gmail.com'
}


}

