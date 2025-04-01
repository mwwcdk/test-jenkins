pipeline {
    agent any  // 必须声明全局 agent 以初始化 WORKSPACE
    environment {
        // 显式定义宿主机路径变量（适配 Windows/Linux）
        HOST_WORKSPACE = "${env.WORKSPACE}".replace('\\', '/')
    }
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'maven:3.9.9-eclipse-temurin-21-alpine'
                    args "-v ${HOST_WORKSPACE}:/jenkins_workspace"
                    reuseNode true
                }
            }
            steps {
                dir('/jenkins_workspace/My-Pipeline_master') {
                    sh 'mvn --version'
                }
            }
        }
    }
}