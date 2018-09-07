pipeline{
    agent any

    parameters{
        string(name: 'tomcat_dev', defaultValue: 'localhost:8090', description: 'Staging Server')
        string(name: 'tomcat_prod', defaultValue: 'localhost:9090', description: 'Production Server')
    }

    tools{
        maven 'localMaven'
    }

    triggers{
        pollSCM('* * * * *')
    }

    stages{
        stage('Build'){
            steps{
                bat 'mvn clean package'
            }

            post{
                success{
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage('Deployments'){
            parallel{
                stage('Deploy to Staging'){
                    steps{
                        echo 'Now deploying to staging...'                        
                    }
                }

                stage('Deploy to Production'){
                    steps{
                        echo 'Now deploying to production...'                        
                    }
                }
            }
        }
    }
}