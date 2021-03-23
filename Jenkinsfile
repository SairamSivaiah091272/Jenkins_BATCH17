node
{
 def mavenHome = tool name: "Maven3.6.3"
 
 properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '5', numToKeepStr: '5')), pipelineTriggers([pollSCM('* * * * *')])])
 
 stage('checkout')
 {
 git branch: 'development', credentialsId: '22255892-da73-4927-b3c5-167d2264e683', url: 'https://github.com/SairamSivaiah091272/maven-web-application.git'

 } 
 
 stage('MavenBuild')
 {
   sh "${mavenHome}/bin/mvn clean package"
 }
 
/*
stage('snaerqube')
 {
     sh "${mavenHome}/bin/mvn sonar:sonar"
 }
 stage('upload build artifacts into nexus')
 {
     sh "${mavenHome}/bin/mvn deploy"
 }
 stage('Deploy application into Tomacat')
 {
   sshagent(['ec2-user']) {
   sh "scp -o strictHostkeyChecking=no targey/maven-web-application.war ec2-user@13.126.121.230: /opt/apache-tomcat-9.0.43/webapps"
 }   
 }
 
 */
 
 stage('EmailNotification')
 {
     emailext body: '''Build is over

     Thanks,
     K.sivaiah
    +91-9885553477''', subject: 'Build Trigger', to: 'k.siva091272@gmail.com'
 }
}
 
 
