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
       
        stage('DeployToProd') {
         
            steps {
                withCredentials([sshUserPrivateKey(credentialsId: "webserver_login")]){
                        sshPublisher(
                             failOnError: true,
                             publishers: [
                                sshPublisherDesc(
                                configName: 'prod',
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
