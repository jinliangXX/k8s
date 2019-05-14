## k8s基础命令
- 使用minikube启动集群 | 第一个命令判断minikube是否安装成功，第二个命令启动集群

    
    minikube version
    minikube start
    

- 使用kubectl和集群交互，并查看版本 | 会显示client和server两个版本号，其中client对应kubectl，server对应Master上的k8s版本。

    
    kubectl version
    


- 查看集群的详情 | 将返回dashboard的连接，即使用界面查看相关属性

    
    kubectl cluter-info
    

- 查看集群中可用的节点（nodes）| 获取可部署应用的节点，节点为物理机或虚拟机

    
    kubectl get nodes
    
- 获取kubectl命令文档 | kubectl的常用格式为： kubectl 动作 方法

    
    kubectl
    

- 部署应用 | 使用kubectl run命令部署应用程序

    
    kubectl run kubernetes-bootcamp --image=gcr.io/google-samples/kubernetes-bootcamp:v1 --port=8080
    
- 删除创建的应用 

    
    kubectl delete deployments --all
    
- 列出所有的deployment

    
    kubectl get deployments
    
- 创建代理使通信转发到集群范围的专用网络

    
    kubectl proxy &
    
- 获取http所有api

    
    curl http://localhost:8001
    
- 获取运行中的pods

    
    kubectl get pods
    
- 查看pod中的容器以及镜像

    
    kubectl describe pods
    
- 查看pod日志

    
    kubectl logs $POD_NAME(具体的pod名)
    
- 在pod中执行命令，例如列出环境

    
    kubectl exec $POD_NAME env
    
- 进入到pod的容器中

    
    kubectl exec -ti $POD_NAME bash
    
- 未deployment创建service服务

    
    kubectl expose deployment/kubernetes-bootcamp --type="NodePort" --port 8080
    
- 列出集群当前运行的service

    
    kubectl get services
    
- 查看service的详细信息（例如开放到外部的端口）

    
    kubectl describe services/kubernetes-bootcamp
     
- 查看pod的标签

    
    kubectl describe deployment 
    
- 使用标签筛选pod、service

    
    kubectl get pods -l label_key_value
    
- 为pod应用新标签

    
    kubectl label pod $POD_NAME
    
- 删除services，使用标签

    
    kubectl delete service -l label_key_value
    
- 扩展deployment的副本

    
    kubectl scale deployments/kubernetes-bootcamp --replicas=4
    
- 缩减deployment的副本

    
    kubectl scale deployment/kubernetes-bootcamp --replicas=2
    
- 滚动更新应用，即升级镜像

    
    kubectl set image deployments/kubernetes-bootcamp kubernetes-bootcamp=jocatalin/kubernetes-bootcamp:v2
    
- 更新回滚

    
    kubectl rollout undo deployments/kubernetes-bootcamp
    
