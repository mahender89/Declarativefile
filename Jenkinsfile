pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/intelliqittrainings/maven.git'
                    }   
                    catch(Exception e1)
                    {
                        mail bcc: 'bcc', body: 'Jenkins is unable to download the dev code from git repo', cc: 'cc', from: '', replyTo: '', subject: 'Download failed ', to: 'mahender.penthala1989@gmail.com'
                        exit(1)
                    }    
               }  
            }
        
        }
        stage('ContinuousBuild_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }   
                    catch(Exception e2)
                    {
                        mail bcc: 'bcc', body: 'Jenkins is unable to download the dev code from git repo', cc: 'cc', from: '', replyTo: '', subject: 'Download failed ', to: 'mahender.penthala1989@gmail.com'
                        exit(2)
                    }    
               }  
            }
        
        }
        stage('ContinuousDeployment_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        deploy adapters: [tomcat9(credentialsId: '902be839-fa39-440a-9446-d61b5f97127b', path: '', url: 'http://172.31.34.182:8080')], contextPath: 'testapp', war: '**/*.war'
                    }   
                    catch(Exception e3)
                    {
                        mail bcc: 'bcc', body: 'Jenkins is unable to download the dev code from git repo', cc: 'cc', from: '', replyTo: '', subject: 'Download failed ', to: 'mahender.penthala1989@gmail.com'
                        exit(3)
                    }    
               }  
            }
        
        }
        stage('ContinuousTesting_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                        sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclarativePipeline1/testing.jar'
                    }   
                    catch(Exception e4)
                    {
                        mail bcc: 'bcc', body: 'Jenkins is unable to download the dev code from git repo', cc: 'cc', from: '', replyTo: '', subject: 'Download failed ', to: 'mahender.penthala1989@gmail.com'
                        exit(4)
                    }    
               }  
            }
        
        }
        stage('ContinuousDelivery_master')
        {
            steps
            {
                script
                {
                    try
                    {
                        deploy adapters: [tomcat9(credentialsId: '902be839-fa39-440a-9446-d61b5f97127b', path: '', url: 'http://172.31.40.14:8080')], contextPath: 'prodapp', war: '**/*.war'
                    }
                    catch(Exception e4)
                    {
                        mail bcc: 'bcc', body: 'Jenkins is unable to download the dev code from git repo', cc: 'cc', from: '', replyTo: '', subject: 'Download failed ', to: 'mahender.penthala1989@gmail.com'
                        exit(4)
                    }
                    
                }
            }
        }
    }
}


