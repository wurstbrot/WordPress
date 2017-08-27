#!groovy

node {
    currentBuild.result = "SUCCESS"
    try {
       stage('Checkout'){
          checkout scm
       }

       stage('Build Docker Image') {
            sh 'docker build -t wordpress .'
       }
       stage('Push Image') {
            sh 'docker tag wordpress registry.local:5000/wordpress:$(git rev-parse HEAD)'
            sh 'docker tag wordpress registry.local:5000/wordpress:latest'
            sh 'docker push registry.local:5000/wordpress:latest'
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
