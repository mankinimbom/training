node('built-in') 
{
    stage('ContinuuousDownload') 
    {
       git 'https://github.com/mankinimbom/maven.git'
    }
    stage('ContinuuousBuild')
    {
        sh 'mvn package'
    }
    stage('ContinuousDeployment')
    {
        deploy adapters: [tomcat9(credentialsId: 'd9e1af03-52ba-48b1-8b18-9082c2a62870', path: '', url: 'http://172.31.88.238:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('ContinuousTesting')
    {
          git 'https://github.com/mankinimbom/testingproject.git'
          sh 'java -jar /var/lib/jenkins/workspace/DevOps/testing.jar'
    }
    stage('ContinuousDelivery')
    {
            deploy adapters: [tomcat9(credentialsId: 'd9e1af03-52ba-48b1-8b18-9082c2a62870', path: '', url: 'http://172.31.88.238:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
    stage('ContinuousMonitor')
    {
        
    }}
