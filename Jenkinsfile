pipeline {
    agent any
    
    // tools {
    //     nodejs 'node'  // 使用全局工具配置中设置的名称
    //     dockerTool 'docker'
    // }
    
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // 构建 Docker 镜像 
                    sh '''docker build -t group16-frontend:latest .
                    kubectl rollout restart deployment/group16-frontend-deployment'''
                }
            }
        }
        
        // stage('Deploy') {
        //     steps {
        //         script {
        //             // 部署到服务器或 Kubernetes 集群
        //             sh 'docker rm -f group16-frontend-container 2>/dev/null || true '
        //             sh 'docker run -d -p 80:80 group16-frontend:latest --name group16-frontend-container' 
        //         }
        //     }
        // }
    }
}

