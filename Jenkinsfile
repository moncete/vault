stage "Check syntax"

node {
    ansiblePlaybook(
        playbook: 'vault.yml',
        extras: '--syntax-check',
        colorized: true
    )
}