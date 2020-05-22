pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh 'chmod +x gradlew'
                sh './gradlew build'
                archiveArtifacts artifacts: 'src/index.html'
            }
        }
        
      stage('DeployToStage') {
            when {
                branch 'master'
            }
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: "webserver_login")]){
                    sshPublisher(
                        failOnError: false,
                         configName: 'staging',
                         transfers: [
                                  
                                        sourceFiles: 'src/**',
                                        removePrefix: 'src/'
                  
                                ]
                          
                            )
                        
                    
                }
            }
         } 
      }
   }
