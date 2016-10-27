// -*- mode: groovy -*-

node {
  try {
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
  } catch(err) {
    currentBuild.result = 'FAILURE'
    throw err
  } finally {
    junit allowEmptyResults: true, testResults: 'backend/build/test-results/test/*.xml'
    if(currentBuild.result == null) {
      currentBuild.result = 'SUCCESS'
    }
    step([$class: 'PhabricatorNotifier', commentOnSuccess: true, commentWithConsoleLinkOnFailure: true])
  }
}
