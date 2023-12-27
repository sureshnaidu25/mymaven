pipeline
{
    agent any
    stages
    {
        stage('contdownload')
        {
            steps
            {
                git 'https://github.com/sureshnaidu25/maven.git'
                
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
                   deploy adapters: [tomcat9(credentialsId: 'a2605af0-7ad6-4896-9e7a-578185622063', path: '', url: 'http://172.31.35.44:8080')], contextPath: 'testapp2', war: '**/*.war'
               }
        }
        stage('Conttesting')
        {
            steps
            {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarativepipeline2/testing.jar'
            }
        }
        stage('Contdeploy')
        {
            steps
            {
               deploy adapters: [tomcat9(credentialsId: 'a2605af0-7ad6-4896-9e7a-578185622063', path: '', url: 'http://172.31.46.54:8080')], contextPath: 'webapp2', war: '**/*.war'
            }
        }
    }
}
