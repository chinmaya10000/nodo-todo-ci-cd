pipeline {
    agent any 
    stages {
        stage("build") {
            steps {
                script {
                    echo "building the application..."
                }
            }
        }
        stage("test") {
            steps {
                script {
                    echo "testing the application..."
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    def dockerCmd = 'docker run -d -p 8000:8000 chinmayapradhan/nodo-todo-app:lts'
                    sshagent(['ec2-server-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@3.137.166.249 ${dockerCmd}"
                    }
                }
            }
        }
    }
}
