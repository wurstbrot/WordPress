#!groovy

node {
    currentBuild.result = "SUCCESS"
    try {
       stage('Checkout'){
          checkout scm
       }

       stage('Build Docker'){
            sh 'docker build -t wordpress .'
       }
       stage('Start container') {
         sh 'docker-compuse kill'
         sh 'docker-compuse rm'
         sh 'docker-compuse up -d'
       }

    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }

}
