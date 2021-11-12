pipeline {
    agent any
    stages {
         stage('CleanWorkspace') {
            steps {
                cleanWs()
            }
     }
        stage('Distro Inf') {
            steps {
                echo 'Gerando as informações da Distro...'
                sh 'echo "Info Distr:\n" > distro.txt'
                sh 'cat /etc/*-release >> distro.txt'
            }
        }
        stage('Kernel Info') {
            steps {
                echo 'Gerando as informações do Kernel....'
                sh 'echo "Info Kernel:\n" > kernel.txt'
                sh 'uname -a >> kernel.txt'
            }
        }
        stage('Users Info') {
            steps {
                echo 'Gerando as infomações dos usuarios....'
                sh 'cat /etc/passwd | cut -d: -f1 > users.txt'
            }
        }
        stage('Package Info') {
            steps {
                echo 'Gerando as informações de pacotes instalados....'
                sh 'dpkg -l > packs.txt '
            }
        }
        stage('Consolidando e gerando relatorio') {
            steps {
                echo 'Gerando relatorio....'
                sh 'cat *.txt | grep -v "assessment" > assessment.txt'
                sh 'date >> assessment.txt'
            }
        }
        stage('Realizando Push para o GIT') {
            steps {
          sh script:'''
          #!/bin/bash
          mkdir /var/tmp/git/
          cd /var/tmp/git
          git clone git@github.com:fernandorberto/assessment-job.git
          sleep 3
          cd assessment-job/
          cp /var/jenkins_home/workspace/scripted-pipeline/assessment.txt .
          git add assessment.txt
          git commit -m "Input arquivo assessment"
          git push origin main
          echo "Arquivo assessment.txt gerado no repositorio git@github.com:fernandorberto/assessment-job.git"
        '''
        }
            }
        }
    }
    post {
            always {
                echo 'Sempre serei executado'
            }
            success {
                echo 'Compilação finalizada com sucesso.'
                
            }
            failure {
                echo 'Pipeline de geração de arquivo assessment não rodou corretamente'
            }
        }


