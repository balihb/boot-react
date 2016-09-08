node {
     stage ('checkout') {
     	   checkout scm
     }

     stage ('npm install') {
     	   sh './gradlew npmInstall'
     }

     stage ('assemble') {
     	   sh './gradlew assemble'
     }

     stage ('check') {
     	   sh './gradlew check'
     }
}