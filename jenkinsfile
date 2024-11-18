node('built-in')
{
   stage('contdownload_payments')
   {
     git 'https://github.com/IntelliqDevops/maven.git'
   }
   stage('contbuild_payments')
   {
       sh 'mvn package'
   }
   stage('contdeployment_payments')
   {
     deploy adapters: [tomcat9(credentialsId: 'new-credentials', path: '', url: 'http://172.31.3.150:8080')], contextPath: 'testapp5', war: '**/*.war'
   }
   stage('conttest_payments')
   {
     git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
     sh 'java -jar /var/lib/jenkins/workspace/scriptedpipeline1/testing.jar'
   }
   stage('contdelivery_paymemnts')
   {
      deploy adapters: [tomcat9(credentialsId: 'new-credentials', path: '', url: 'http://13.235.90.142:8080')], contextPath: 'prodapp5', war: '**/*.war'
   }
}

