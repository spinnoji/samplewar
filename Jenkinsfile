pipeline
{
    agent any
	tools
	{
	 jdk 'JAVA_HOME'
	 maven 'MAVEN_HOME'
	}
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                checkout scm
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
		sshagent(['ssh-credentials']) {
                sh 'scp -o StrictHostKeyChecking=no /var/lib/jenkins/workspace/sample1/webapp/target/hello-world-war-1.0.0.war ec2-user@172.31.25.70:/usr/local/tomcat/webapps/'
            }
	    }
        }
		
		
    }
}
