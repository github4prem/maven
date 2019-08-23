node('master')
{
    stage('ContinuousDownload')
    {
       git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild')
    {
        sh label: '', script: 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scmpipeline/webapp/target/webapp.war ubuntu@172.31.42.164:/var/lib/tomcat8/webapps/testapp2.war'
    }
    stage('ContinuousTesting')
    {
        git 'https://github.com/selenium-saikrishna/FunctionalTesting.git'
        sh label: '', script: 'echo "Testing Passed"'
    }
    stage('ContinuousDelivery')
    {
         sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scmpipeline/webapp/target/webapp.war ubuntu@172.31.34.107:/var/lib/tomcat8/webapps/prodapp.war'
    }
}
