pipeline{
  agent any
  tools{
    maven "local_maven"
  }
  stages{
    stage('Build'){
      steps{
        sh 'mvn Clean package'
      }
      post{
        success{
          echo "Archiving the Artifacts"
          archiveArtifacts artifacts: '**/target/*.war'
        }
      }
    }
    stage ('Deploy to tomcat server'){
      steps{
        deploy adapters: [tomcat9(credentialsId: '8cf04771-ab19-4a90-b832-579207072c7d', path: '', url: 'http://16.16.170.169:8080/')], contextPath: null, war: '**/*.war'
      }
    }
  }
}