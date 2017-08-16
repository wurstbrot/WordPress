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
         sh 'docker-compose kill'
         sh 'docker-compose rm'
         sh 'docker-compose up -d'
       }

    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }

}
