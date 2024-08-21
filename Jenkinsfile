pipeline {
    agent any
    
    tools {
        nodejs 'node'  // 使用全局工具配置中设置的名称
        dockerTool 'docker'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // 拉取代码仓库
               sh "git 'https://github.com/PLUTOFX/BUAA-SE-2024Spring-Group16-FrontEnd.git'"
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // 构建 Docker 镜像
                    sh 'docker build -t group16-frontend:latest .'
                }
            }
        }
        
        // stage('Push Docker Image') {
        //     steps {
        //         script {
        //             // 登录到 Docker Registry（如果需要）
        //             sh 'docker login -u your-username -p your-password'
                    
        //             // 推送 Docker 镜像到 Docker Registry
        //             sh 'docker tag your-image-name:latest your-repo/your-image-name:latest'
        //             sh 'docker push your-repo/your-image-name:latest'
        //         }
        //     }
        // }
        
        stage('Deploy') {
            steps {
                script {
                    // 部署到服务器或 Kubernetes 集群
                    sh 'docker run -d -p 80:80 group16-frontend:latest --name group16-frontend-container' 
                }
            }
        }
    }
}

