stage "Check syntax"

node {
    ansiColor('xterm') {
        customWorkspace '/tmp'
        ansiblePlaybook(
            playbook: '/execute/git/vault.yml',
            extras: '--syntax-check',
            colorized: true
        )
    }   
}