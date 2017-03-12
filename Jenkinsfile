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
          projectName: 'rebaser/master']);
  sh 'ls -la'
  sh 'git rebase --onto `cat commit-id.txt` origin/master'
}
