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
                deploy adapters: [tomcat9(credentialsId: '5b6c9c37-8a81-427c-b155-6804ef96242a', path: '', url: 'http://172.31.34.138:8080')], contextPath: 'prod1', war: '**/*.war'
            }
        }
        
        
        
        
    }
}
