stage "Check syntax"

node {
    deletedir()
    checkout scm
    ws ('/tmp/') {
        ansiColor('xterm') {
            ansiblePlaybook(
                playbook: '/execute/git/vault.yml',
                extras: '--syntax-check',
                colorized: true
            )
        }
    }
}