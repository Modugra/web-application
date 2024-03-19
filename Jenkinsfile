pipeline
{
    agent any
    tools{
        maven "Maven"
    }
      stages{
        stage('pulling code'){
            steps{
                git branch: 'main' , url: 'https://github.com/Modugra/Rigstration-Form.git'
            }
        }
         
         stage('Package'){
            steps{
                sh 'mvn package'
           }
        }
        
        stage('Deploy App in Appserver'){
             steps{
                echo "Deploy App in AppServer"
               deploy adapters: [tomcat9(credentialsId: 'Tomcat', path: '', url: 'http://16.16.187.106:8080')], contextPath: null, war: '**/*.war'
            }
        }
          
    }
}
