def ent = env.BRANCH_NAME //Variable para elegir el entorno de ejecucion

pipeline {
    
    agent any

    stages {
        stage('Check syntax') {
            steps {
                ansiColor('xterm') {
                    ansiblePlaybook (
                        playbook: 'vault.yml',
                        extras: '--syntax-check',
                        credentialsId: 'f702de34-19dc-4840-a8d1-2f7e1857f4d4',
                        sudo: true,
                        sudoUser: 'jenkins',
                        colorized: true
                    )
                }
            }
        }

        stage('Run Playbook') {
            steps {
                echo "Trabajando en el entorno de ${ent}"
                ansiColor('xterm') {
                    ansiblePlaybook (
                        playbook:  'vault.yml',
                        credentialsId: 'f702de34-19dc-4840-a8d1-2f7e1857f4d4',
                        extraVars: [ ENV: "${ent}" ],
                        become: true,
                        becomeUser: 'jenkins',
                        colorized: true
                    )
                }

            }
        }
    }

    post {
        success {
            emailext (
                from: 'test@leroymerlin.es',
                to: 'jose-ramon.rodriguez@ext.leroymerlin.es',
                subject: "Ejecucion en ${ent} '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                body: "EXECUCION EXITOSA"
            )
        }
    }
}        


