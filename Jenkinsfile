pipeline {
    agent any  // 必须声明全局 agent 以初始化 WORKSPACE
    environment {
        // 替换反斜杠为 Linux 路径格式，并强制全小写
        HOST_WORKSPACE = "/${env.WORKSPACE.replaceAll('\\\\', '/').replace(' ', '_').toLowerCase()}"
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
                    sh "docker run --rm -v ${HOST_WORKSPACE}:/test alpine ls /test"
                }
            }
        }
    }
}