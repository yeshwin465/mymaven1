pipeline
{
    agent any
    stages
    {
        stage('contionous download')
        {
            steps
            {
                git 'https://github.com/yeshwin465/maven.git'
            }
        }
        stage('contionous build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('contionous deployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '4f4f05da-1c2a-400c-aca8-2bf1659cb538', path: '', url: 'http://172.31.46.51:8080')], contextPath: 'testapps', war: '**/*.war'
            }
        }
        stage('contionous testing')
        {
            steps
            {
                git 'https://github.com/yeshwin465/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/Declarativepipeline/testing.jar'
            }
            
        }
        stage('contionous delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '4f4f05da-1c2a-400c-aca8-2bf1659cb538', path: '', url: 'http://172.31.45.166:8080')], contextPath: 'prodapps', war: '**/*.war'
            }
        }
        
        
        
    }
}
