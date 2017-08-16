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
         sh 'docker-compose kill wordpress'
         sh 'docker-compose rm -f wordpress'
         sh 'docker-compose up -d'
       }

    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }

}
