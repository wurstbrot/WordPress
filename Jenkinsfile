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

    }
    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }

}
