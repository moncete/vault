stage "Check syntax"

node {
    label 'some-label'
    customWorkspace '/tmp'
    ansiColor('xterm') {
        ansiblePlaybook(
            playbook: '/execute/git/vault.yml',
            extras: '--syntax-check',
            colorized: true
        )
    }   
}