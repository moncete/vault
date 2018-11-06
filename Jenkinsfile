stage "Check syntax"

node {
    ansiColor('xterm') {
        label 'some-label'
        customWorkspace '/tmp'
        ansiblePlaybook(
            playbook: '/execute/git/vault.yml',
            extras: '--syntax-check',
            colorized: true
        )
    }   
}