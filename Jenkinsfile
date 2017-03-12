stage('commit') {
  node {
    echo 'hello'
    cleanCheckout()
    sh 'ls -la'
  }
}

def cleanCheckout() {
  deleteDir()
  checkout scm
  step ([$class: 'CopyArtifact',
          projectName: 'master-archive-commit-id']);
  sh 'git rebase --onto origin/master~1 origin/master'
  sh 'ls -la'
}
