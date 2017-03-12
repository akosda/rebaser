buildMarkedAsFailed = false

withPostActions(['archiveCommitId']) {
	stage('compile') {
		node {
      echo 'hello'
		}
	}
}

def cleanCheckout() {
	deleteDir()
	checkout scm
}

def withPostActions(actions, body) {
  try {
    body.call()
  } catch (e) {
    buildMarkedAsFailed = true
    throw e
  } finally {
    for (action in actions) {
      echo "executing action $action"
      "${action}"()
    }
  }
}

def archiveCommitId() {
	if(!buildMarkedAsFailed) {
		node {
			cleanCheckout()
			sh 'git log -1 --format="%H" > commit-id.txt'
			archiveArtifacts artifacts: 'commit-id.txt', onlyIfSuccessful: true
		}
	}
}
