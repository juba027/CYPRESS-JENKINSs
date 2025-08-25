pipeline{
    agent{
        docker{
            image "cypress/browsers.lastest"
            args '--entrypoint='
            
        }
    }
    stages{
        stage('test stage'){
            steps{
                echo 'hello from jenkins file'
            }
        }
        stage('install dependance'){
            steps{
                sh 'npm ci'
            }
        }
        stage('test'){
            steps{
                sh 'npx cypress run'
            }
        }

    }
}