pipeline{
    agent any

    tools{
        maven 'localMaven'
    }

    stages{
        stage('Build'){
            steps{
                bat 'clean package'
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