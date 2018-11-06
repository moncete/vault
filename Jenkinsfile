stage "Check syntax"

node {
    deleteDir()
    //checkout scm
    ansiColor('xterm') {
        ansiblePlaybook(
            playbook: '/execute/git/vault.yml',
            extras: '--syntax-check',
            colorized: true
        )
    }
}
