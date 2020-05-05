node
{
    def mavenhome = tool name: "maven3.6.3"
    
    stage ('checkout')
    {
        git branch: 'master', credentialsId: '42bb6128-0d7a-4154-a9c7-bc969a3d530a', url: 'https://github.com/SairamSivaiah091272/maven-web-application.git'
        
    }
    stage ('build')
    {
        sh "${mavenhome}/bin/mvn clean package"
        
    }
    
    stage ('ExicuteSonarQube Report')
    {
        sh "${mavenhome}/bin/mvn sonar:sonar"
    }
    stage ('Upload Build artfacts to sonatype')
    {
        sh "${mavenhome}/bin/mvn deploy" 
    }
    */
    stage ('Deploy appinto tomcat')
    {
        sshagent(['7d2b913d-7877-4527-9823-ab32f881fac3']) {
            sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@18.191.141.237://opt/apache-tomcat-9.0.34/webapps"
    
     }
    }
    stage ('Email notification')
    {
    emailext body: '''Build Over!!

    Best regards,
    Sampatsivaiah.
    +91-9885553477''', subject: 'Build over!!!', to: 'shiva091272@gmail.com'
   } 
 */
      
}
