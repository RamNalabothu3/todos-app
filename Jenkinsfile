pipeline{
    agent any

    tools{
        nodejs "nodejs"
    }

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
                    sh 'nohup yarn start > app.log 2>&1 &'
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
