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
  sh 'git rebase master'
}
