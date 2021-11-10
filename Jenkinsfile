pipeline {
    agent any
    environment {
        NOME = 'Vinicius'
        SOBRENOME = 'Cavalcanti'
    }
    stages {
        stage('Distro Inf') {
            steps {
                echo 'Coletando as informações da Distro...'
                sh 'cat /etc/*-release > distro.txt'
            }
        }
        stage('Kernel Info') {
            steps {
                echo 'Coletando as informações do Kernel'
                sh 'uname -a > kernel.txt'
            }
        }
        stage('Users Info') {
            steps {
                echo 'Coletando as infomações dos usuarios..'
                sh 'cat /etc/passwd | cut -d: -f1 > users.txt'
            }
        }
        stage('Juntando') {
            steps {
                echo 'Jutando relatorios'
                sh 'cat *.txt > asses.txt '
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
    post {
            always {
                echo 'Sempre serei executado'
            }
            success {
                echo 'Serei executado apenas quando a pipeline fechar com sucesso'
            }
            failure {
                echo 'Serei executado apenas quando a pipeline fechar com erro'
            }
        }
}
