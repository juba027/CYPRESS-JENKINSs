pipeline {
  agent {
    docker {
      image 'cypress/browsers:latest'   
      args '--entrypoint='              
      reuseNode true
    }
  }
  options { timestamps(); ansiColor('xterm') }

  stages {
    stage('Checkout'){ steps { checkout scm } }

    stage('Install deps'){
      steps { sh 'npm ci' }             
    }

    stage('Run Cypress'){
      steps { sh 'npx cypress run' }
    }
  }

  post {
    always {
      archiveArtifacts artifacts: 'cypress/**/*', allowEmptyArchive: true
      junit allowEmptyResults: true, testResults: 'cypress/**/results*.xml'
    }
  }
}
