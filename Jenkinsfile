pipeline{
    agent any

    stages{

        stage('Install packages'){
            steps{
                script{
                    sh  'yarn install'
                }
            }
        }

        stage('Run the app'){
            steps{
                script{
                    sh 'yarn start &'
                    sleep 5 
                }
            }
        }

        stage('health check'){
            steps{
                script{
                    sh 'curl http://localhost:3000/health'
                }
            }
        }

        stage('cleanUp'){
            steps{
                script{
                    sh 'pkill -f "node"'
                }
            }
        }
    }
}
