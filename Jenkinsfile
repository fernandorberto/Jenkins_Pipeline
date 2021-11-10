pipeline {
    agent any
    environment {
        NOME = 'Vinicius'
        SOBRENOME = 'Cavalcanti'
    }
    stages {
        stage('Distro Inf') {
            steps {
                echo 'Coletando as informações da Distro'
                sh 'cat /etc/*-release > distro.txt'
            }
        }
        stage('Kernel Info') {
            steps {
                echo 'Coletando as informações do Kernel'
                sh ''
                sh 'cat /etc/*-release > kernel.txt'
            }
        }
        stage('Juntando') {
            steps {
                echo 'Testing..'
                sh 'kernel.txt >> distro.txt'
                sh 'pwd'
                sh 'ls -la'
            }
        }
        stage('Reports') {
            steps {
                echo 'Reports..'
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
