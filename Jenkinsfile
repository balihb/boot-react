node {
     stage ('checkout') {
     	   checkout scm
     }

     stage ('assemble') {
     	   sh './gradlew assemble'
     }

     stage ('check') {
     	   sh './gradlew check'
     }
}