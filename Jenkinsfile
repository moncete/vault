stage "Check syntax"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
        ansiblePlaybook(
            laybook: 'vault.yml',
            extras: '--syntax-check',
            colorized: true
        )
    }
  
}