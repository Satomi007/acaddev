pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sudo sh './gradlew build'
                archiveArtifacts artifacts: 'src/index.html'
            }
        }
    }
       
}
