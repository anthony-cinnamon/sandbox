node {
    checkout scm
    // GIT_BRANCH = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
    if (BRANCH_NAME.contains('evaluation')) {
        stage('test') {
            sh "echo ${env.BRANCH_NAME}"
            sh 'echo testing'
        }
    } else {
        stage('no-test') {
            sh 'echo "No test"'
            sh "echo ${env.BRANCH_NAME}"
        }
    }
}

