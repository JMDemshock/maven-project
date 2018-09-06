pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                sh 'mvn clean package'
            }

            post{
                success{
                    echo 'Now Archiving...'
                    archiveArtifact artifacts: '**/target/*.war'
                }
            }
        }
    }
}