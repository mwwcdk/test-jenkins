pipeline {
    agent any  // 必须声明全局 agent 以初始化 WORKSPACE
    environment {
        // 使用 replaceAll 彻底替换路径中的反斜杠和空格
        HOST_WORKSPACE = "\"${env.WORKSPACE.replaceAll('\\\\', '/').toLowerCase()}\""
    }
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'maven:3.9.9-eclipse-temurin-21-alpine'
                    args "-v ${HOST_WORKSPACE}:/jenkins_workspace -w /jenkins_workspace"
                    reuseNode true
                }
            }
            steps {
                script {
                    echo "宿主机路径：${HOST_WORKSPACE}"
                }
                dir('/jenkins_workspace') {
                    sh 'pwd && ls -al'
                }
            }
        }
    }
}