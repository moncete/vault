stage "Check syntax"

node {
    
        ansiColor('xterm') {
            ws ('/tmp/') {
            ansiblePlaybook(
                playbook: '/execute/git/vault.yml',
                extras: '--syntax-check',
                colorized: true
            )
            }
        }
}