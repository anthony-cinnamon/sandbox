node {
    checkout scm
    // GIT_BRANCH = sh(returnStdout: true, script: 'git rev-parse --abbrev-ref HEAD').trim()
    COMMIT_MSG = sh(script: "git log -1 | grep 'jenkins:evaluate'", returnStatus: true)
    stage('normal') {
            sh 'echo normal_build'
    }
    if (COMMIT_MSG != 0) {
        stage('test') {
            sh 'echo do_test'
        }
    }
    // if (BRANCH_NAME.contains('evaluation')) {
    //     stage('test') {
    //         sh "echo ${env.BRANCH_NAME}"
    //         sh 'echo testing'
    //     }
    // } else {
    //     stage('no-test') {
    //         sh 'echo "No test"'
    //         sh "echo ${env.BRANCH_NAME}"
    //     }
    // }
}

