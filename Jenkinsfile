pipeline{
    agent none
    stages{
        stage('Check syntax'){
            steps{
                    ansiColor('xterm') {
                        ansiblePlaybook(
                            playbook: '/execute/git/vault.yml',
                            extras: '--syntax-check',
                            credentialsId: 'f702de34-19dc-4840-a8d1-2f7e1857f4d4',
                            sudo: true,
                            sudoUser: 'jenkins',
                            colorized: true
                        )
                    }
            }
        }
    }
}        


