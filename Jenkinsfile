stage "Check syntax"

node {
    dir ('/tmp') {
        ansiColor('xterm') {
            ansiblePlaybook(
                playbook: '/execute/git/vault.yml',
                extras: '--syntax-check',
                credentialsId: 'private_key',
                colorized: true
            )
        }
    }
}


stage "Execute dry run"

node{
    ansiColor('xterm') {
        ansiblePlaybook(
            playbook: '/execute/git/vault.yml'
            credentialsId: 'private_key'
            extras: '--check --diff'
            colorized: true
        )
}
