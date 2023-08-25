node('built-in')
{
    stage('ContinuousDownload')
    {
          git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild')
    {
          sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
          deploy adapters: [tomcat9(credentialsId: 'e5a0f6b1-fd7e-424a-9bbc-22a946de37c2', path: '', url: 'http://172.31.47.134:8080')], contextPath: 'app1', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
          git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
          sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptedPipeline1/testing.jar'
    }
    stage('ContinuousDelivery')
    {
          deploy adapters: [tomcat9(credentialsId: 'e5a0f6b1-fd7e-424a-9bbc-22a946de37c2', path: '', url: 'http://172.31.35.97:8080')], contextPath: 'prod', war: '**/*.war'
    }
}
