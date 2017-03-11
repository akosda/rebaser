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
  sh 'git rebase --onto origin/master~1 origin/master'
}
