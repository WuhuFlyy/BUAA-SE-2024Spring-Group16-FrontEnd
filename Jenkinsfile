pipeline {
    agent any
    
    // tools {
    //     nodejs 'node'  // 使用全局工具配置中设置的名称
    //     dockerTool 'docker'
    // }
    
    stages {

        stage('拉取代码') {
              steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [],
                userRemoteConfigs: [[credentialsId: 'e82aa310-3ca3-44b6-8493-d820df7c8f6c', url:
                'https://github.com/WuhuFlyy/BUAA-SE-2024Spring-Group16-FrontEnd']]])
              }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // 构建 Docker 镜像 
                    sh '''

                    kubectl delete -f deployment_frontend.yaml || true
                    docker rmi -f group16-frontend:latest || true
                    docker build -t group16-frontend:latest .
                    kubectl apply -f deployment_frontend.yaml ||true
                    '''
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

