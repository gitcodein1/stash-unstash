pipeline {
  agent none
  stages {
    stage("STAGE1") {
      agent {
        label 'docker-node1'
      }
      steps {
        sh 'sh script.sh 100 200 | xargs -I {} sh output.sh {} > result.txt'
        sh 'ls -l'
        sh 'cat result.txt'
        stash includes: 'result.txt', name: 'stage1-stash'
      }
    }
    stage("STAGE2") {
      agent {
        label 'docker-node2'
      }
      steps {
        unstash 'stage1-stash'
        sh 'ls -l'
        sh 'cat result.txt'
      }
    }
  }
}
