node {
    checkout scm
    GIT_BRANCH = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
    if (GIT_BRANCH.contains('evaluation')) {
        stage('test') {
            sh "echo ${GIT_BRANCH}"
        }
    } else {
        stage('no-test') {
            sh 'echo "No test"''
        }
    }
}

