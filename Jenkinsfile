stage "Check syntax"

node {
    wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]){
        ansiblePlaybook(
            laybook: 'vault.yml',
            //inventory: 'inventory.ini',
            //credentialsId: '96b3fe82-e6a4-45eb-9e8d-0a512cba5a9c',u
            extras: '--syntax-check',
            colorized: true
        )
    }
  
}