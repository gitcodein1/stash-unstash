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
      }
    }
    stage("STAGE2") {
      agent {
        label 'docker-node2'
      }
      steps {
        sh 'ls -l'
        sh 'cat result.txt'
      }
    }
  }
}
