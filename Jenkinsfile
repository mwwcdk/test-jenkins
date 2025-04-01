pipeline {
    agent any  // 必须声明全局 agent 以初始化 WORKSPACE
    environment {
        // 处理路径大小写和空格（Windows 需双引号包裹）
        HOST_WORKSPACE = "\"${env.WORKSPACE.replace('\\', '/').toLowerCase()}\""
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