node {
    checkout scm
    stage('test') {
        def rootPassword = '123456a@'
        def initDatabaseName = 'test'
        def initDatabase = "${env.WORKSPACE}" + '/' + 'test_db.sql'

        withEnv(["MYSQL_ROOT_PASSWORD=${rootPassword}", "MYSQL_DATABASE=${initDatabaseName}"]) {
            docker.image('mariadb:10.4').withRun("-e MYSQL_ROOT_PASSWORD -e MYSQL_DATABASE -v ${initDatabase}:/docker-entrypoint-initdb.d/init.sql") { c ->
                sh "docker exec ${c.id} cat /docker-entrypoint-initdb.d/init.sql"
                sh "docker logs -f ${c.id}"
                docker.image('mariadb:10.4').inside("--link ${c.id}:db") {
                    /* Wait until mysql service is up */
                    sh 'while ! mysqladmin ping -hdb --silent; do sleep 1; done'
                }
            }
        }
    }
}

