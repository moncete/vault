stage "Check syntax"

node {
    dir ('/tmp') {
        ansiColor('xterm') {
            ansiblePlaybook(
                playbook: '/execute/git/vault.yml',
                //extras: '--syntax-check',
                colorized: true
            )
        }
    }
}
