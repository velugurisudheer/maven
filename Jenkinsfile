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
      deploy adapters: [tomcat9(credentialsId: '1b0cb347-0314-4ecb-8ff9-b4cd288b3404', path: '', url: 'http://172.31.40.137:8080')], contextPath: 'testapp', war: '**/*.war'
   }
stage('ContinuousTesting') 
   {
      git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
      sh 'java -jar /var/lib/jenkins/workspace/Scriptedpipeline/testing.jar'
      
   }
stage('ContinuousDelivery') 
   {
       input message: 'need approval from DM', submitter: 'tarun'
      deploy adapters: [tomcat9(credentialsId: '1b0cb347-0314-4ecb-8ff9-b4cd288b3404', path: '', url: 'http://172.31.47.225:8080')], contextPath: 'prodapp', war: '**/*.war'  
   }


}
