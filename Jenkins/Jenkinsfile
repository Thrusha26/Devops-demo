pipeline{
    agent any

    stages{
        stage("Server Details"){
            steps{
                echo "Server Details"
            }
        }
        stage("CPU Details"){
            steps{
                sh 'ls cpu'
            }
        }
        stage("Memory Details"){
            steps{
                sh 'free -h'
            }
        }
        stage("Disk Details"){
            steps{
                sh 'df -h'
            }
        }
        stage("Network Details"){
            steps{
                sh 'ifconfig'
            }
        }
        stage("IP Address Details"){
            steps{
                sh 'hostname -I'
            }
        }
    }
}
