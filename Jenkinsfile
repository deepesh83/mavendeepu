pipeline{
    agent any

    tools {
         maven 'maven'
         jdk 'java'
    }

    stages{
          stage('build'){
            steps{
               bat 'mvn clean package'
              }
         post{
             success{
                    echo "Archive the File"
                    archiveArtifacts artifacts:'**/target/*.jar'
                     }
               }
              
             }

        
        stage('Deploy to tomcat server'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'e2f497ff-8027-4ca5-b2f9-8adef7bbb8a4', path: '', url: 'http://localhost:8082/')], contextPath: null, war: '**/*.jar'
               }
            }
      
         }
}
