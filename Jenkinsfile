/* Requires the Docker Pipeline plugin */
// pipeline {
//     agent { docker { image 'maven:3.9.9-eclipse-temurin-21-alpine' } }
//     stages {
//         stage('build') {
//             steps {
//                 sh 'mvn --version'
//             }
//         }
//     }
// }

// pipeline {
//     agent {
//         docker {
//             image 'maven:3.9.9-eclipse-temurin-21-alpine'
//             // 关键参数优化
//             args '-v /d/Program\ Files/Jenkins/.jenkins/workspace:/jenkins_workspace'  // 路径转义处理
//             reuseNode true  // 强制使用同一节点（网页1）
//         }
//     }
//     stages {
//         stage('build') {
//             steps {
//                 dir('/jenkins_workspace/My-Pipeline_master') {  // 容器内绝对路径
//                     sh 'mvn --version'
//                 }
//             }
//         }
//     }
// }

pipeline {
    agent {
        docker {
            image 'maven:3.9.9-eclipse-temurin-21-alpine'
            // 修正路径转义方式（两种方案）
            args "-v /d/Program\\ Files/Jenkins/.jenkins/workspace:/jenkins_workspace"  // 使用双反斜杠转义
            // 或改用正斜杠避免转义（推荐）
            // args "-v /d/Program Files/Jenkins/.jenkins/workspace:/jenkins_workspace"
            reuseNode true
        }
    }
    stages {
        stage('build') {
            steps {
                dir('/jenkins_workspace/My-Pipeline_master') {
                    sh 'mvn --version'
                }
            }
        }
    }
}