stage "Check syntax"

node {
    ansiColor('xterm') {
        ansiblePlaybook(
            playbook: '/execute/git/vault.yml',
            extras: '--syntax-check',
            colorized: true
        )
    }   
}