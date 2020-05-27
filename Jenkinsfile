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
       
        stage('DeployToDev') {
          
            
            steps {
                
                withCredentials([sshUserPrivateKey(credentialsId: "webserver_login")]){
                        sshPublisher(
                             failOnError: true,
                             publishers: [
                                sshPublisherDesc(
                                configName: 'dev',
                                    if (failOnError: true) {
                                       output 'couldnt make ssh connection, Please check instance status' 
                                    }
                               
                                transfers: [
                                    sshTransfer(
                                        sourceFiles: 'src/**',
                                        removePrefix: 'src/'
                                    )
                                ]
                            )
                        ]
                    )
                } 
              
           }  
        }
    }
}
