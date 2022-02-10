pipeline
{
    agent any
    stages
    {
         stage('ContineousDownload')
         {
             steps
             {
                        git 'https://github.com/intelliqittrainings/maven.git' 
             }
         }
         stage('ContineousBuild')
         {
             steps
             {
                      sh 'mvn package'
             }
         }
         stage('ContineousDeployement')
         {
             steps
             {
                      deploy adapters: [tomcat9(credentialsId: '8a24f55c-6514-4e7a-8f6b-06aeb3b5cd2a', path: '', url: 'http://172.31.30.129:8080')], contextPath: 'amma', war: '**/*.war'
             }
         }
         stage('ContineousTesting')
         {
             steps
             {
                      git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                      sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline/testing.jar'
             }
         }
         stage('ContineousDelivery')
         {
             steps
             {
                      
                      deploy adapters: [tomcat9(credentialsId: '9398b3b3-7682-4e58-a40f-36aa8e83ab99', path: '', url: 'http://172.31.24.147:8080')], contextPath: 'nanna', war: '**/*.war'
             }
         }
    }

}
