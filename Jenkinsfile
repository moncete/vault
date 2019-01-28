def ent = env.BRANCH_NAME //Variable para elegir el entorno de ejecucion

pipeline {
    
    //agent { label 'DocAnsi' }
    agent none

    environment {
        JUNIT_OUTPUT_DIR = './test'
    }


    stages {

        stage('Test Molecule'){

            agent { label 'Molecule' }

            environment {
                JUNIT_OUTPUT_DIR = './test'
            }
            
            steps {
                sh '''
                ls -l
                ansible --version
                '''                
            }
        }

        stage('Check syntax') {

            agent { label 'DocAnsi' }

            steps {
                ansiColor('xterm') {
                    ansiblePlaybook (
                        playbook: 'vault.yml',
                        inventory: 'inventario',
                        extras: '--syntax-check',
                        credentialsId: 'f702de34-19dc-4840-a8d1-2f7e1857f4d4',
                        become: true,
                        becomeUser: 'root',
                        colorized: true
                    )
                }
            }

        stage('Copy File') {

            agent { label 'DocAnsi' }
            environment {
                JUNIT_OUTPUT_DIR = './test'
            }           

            steps {
                sh '''
                 mkdir test
                '''
                echo "Trabajando en el entorno de ${ent}"
                ansiColor('xterm') {
                    ansiblePlaybook (
                        playbook:  'vault.yml',
                        inventory: 'inventario',
                        credentialsId: 'f702de34-19dc-4840-a8d1-2f7e1857f4d4',
                        disableHostKeyChecking: true,
                        extraVars: [ ENV: "${ent}" ],
                        become: true,
                        becomeUser: 'root',
                        colorized: true
                    )
                }

            }
            post {
                always{
                    junit 'test/*.xml'
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
                attachLog: true,
                body: """<p>STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
              <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>"""
            )
        }
        
        failure {
            emailext (
                from: 'test@leroymerlin.es',
                to: 'jose-ramon.rodriguez@ext.leroymerlin.es',
                subject: "Ejecucion en ${ent} '${env.JOB_NAME} [${env.BUILD_NUMBER}]'",
                attachLog: true,
                body: """<p>FAIL: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]':</p>
              <p>Check console output at &QUOT;<a href='${env.BUILD_URL}'>${env.JOB_NAME} [${env.BUILD_NUMBER}]</a>&QUOT;</p>"""
            )

        }
    }
}