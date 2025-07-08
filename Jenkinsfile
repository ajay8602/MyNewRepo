pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
               script {
                    if (env.CHANGE_ID) {
                        echo "This build was triggered by a PR: #${env.CHANGE_ID}"
                        echo "PR Title: ${env.CHANGE_TITLE}"
                        echo "From: ${env.CHANGE_BRANCH} → To: ${env.TARGET_BRANCH}"
                    } else {
                        echo "This is a normal branch build: ${env.BRANCH_NAME}"
                    }
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Simulate success or failure
                    def buildSuccess = true
                    if (buildSuccess) {
                        githubNotify context: 'CI Status', status: 'SUCCESS', description: 'Build passed 🎉'
                    } else {
                        githubNotify context: 'CI Status', status: 'FAILURE', description: 'Build failed ❌'
                    }
                }
            }
        }
    }
}
