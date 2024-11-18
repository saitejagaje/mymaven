pipeline
{
  agent any
  stages
  {
    stage('contdownload_loans')
    {
      steps
      {
         git 'https://github.com/IntelliqDevops/maven.git'
      }
    }
  
   stage('contbuild_loans')
        {
            steps
            {
               sh 'mvn package'
            }
        }
    stage('contdeploy_loans')
         {
             steps
             {
                 deploy adapters: [tomcat9(credentialsId: 'new-credentials', path: '', url: 'http://172.31.3.150:8080')], contextPath: 'testapp3', war: '**/*.war'
             }
         }
         stage('conttesting_loans')
            {
                steps
                {
                    git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
                    sh 'java -jar /var/lib/jenkins/workspace/declaritivepipeline1/testing.jar'
                }
            }
    }
}
