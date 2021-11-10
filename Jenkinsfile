pipeline {
    agent any
    environment {
        NOME = 'Vinicius'
        SOBRENOME = 'Cavalcanti'
    }
    stages {
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
                sh 'cat *.txt > assessment.txt'
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
                echo 'Serei executado apenas quando a pipeline fechar com erro'
            }
        }
}
