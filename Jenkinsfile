node('master') 
{
    stage('ContinuousDownload')
    {
        git 'https://github.com/intelliqittrainings/mymaven1234.git'             
    }
    stage('ContinuousBuild')
    {
        sh 'cd /home/ubuntu/.jenkins/workspace/ScriptedPipeline;mvn package'
    }
    stage('ContinuousDeployment')
    {
sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.30.223:/var/lib/tomcat9/webapps/testapp.war'
    }

    stage('ContinuousTesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
    }
    stage('ContinuousDelivery')
    {
    
    sh 'scp /home/ubuntu/.jenkins/workspace/ScriptedPipeline/webapp/target/webapp.war ubuntu@172.31.31.112:/var/lib/tomcat9/webapps/prodapp.war'}
}

