pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/krishnain/maven16.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
sh '''scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.36.141:/var/lib/tomcat9/webapps/testapp.war
'''
	    }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/DeclarativePipeline1/testing.jar'
            }
        }
        stage('ContinuousDelivery')
        {
            steps
            {
            
sh '''scp /var/lib/jenkins/workspace/DeclarativePipeline1/webapp/target/webapp.war ubuntu@172.31.34.138:/var/lib/tomcat9/webapps/prodapp.war
'''
	    }
        }
        
        
        
        
    }
}
